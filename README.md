# template

**change value in queue**: 
```c++
auto& curr = q.front();
--curr.first;
if (!curr.first) q.pop();
 ```

**get number of digits** : ``int(log10(num) + 1) //log10(7666) is 3..... +1 = 4`` 

**string to int** ``stoi(num);``

**char to int**: ``c -'0'``

**number of sublist**: ``res += (1+cnt)*cnt/2``

**priority_queue**: ``(<: 4321, >: 1234)`` <br/>
```c++ 
priority_queue<int, vector<int>, greater<int>> pq; // 1234
```
```c++
auto comp = []( pair<int,int>  a, pair<int,int>  b) { return a.second > b.second; };
priority_queue< pair<int,int> , vector<pair<int,int>>, decltype(comp) > pq( comp );
```

**sort**``(>: 4321, <: 1234)`` 
```c++
std::sort(s.begin(), s.end(), std::greater<int>()); // 4321 

sort(costs.begin() , costs.end() , [](vector<int>& a,vector<int>& b) -> bool{  // sort by difference between v[1]-v[0] largest to smallest
   return a[1]-a[0] > b[1]-b[0];
});
```

**list**
```c++
 #include <list>
 list <pair<int, int>> li;
 std::list<char> letters {'o', 'm', 'g', 'w', 't', 'f'};
 letters.back(); letters.front();
 push_back()/push_front()
 pop_front()/pop_back()
 ```
 
**bitset**
```c++
 bitset<64> nums(start);
 bitset<64>nums2(end);
 nums =  nums<<1; // shift left add a zero in the back not 1
 nums|= one; 
```

**stringstream split**
```c++
std::string input = "abc,def,ghi";
std::istringstream ss(input);
std::string token;

while(std::getline(ss, token, ',')) {
    std::cout << token << '\n';
}
```

**auto in map**
```c++
for(auto k: umap){
        if(s.find(k.second)==s.end()){
            s.insert(k.second);
        }
        else{
            return false;
        }
    }
```

**count how many ones are in binary**
```c++
    int n = 20;
    int count =0;
    int one = 1;
  
    for(int i=0;i<32;i++){
         one = 1<<i;
        if(n&one){
            count++;
           
        }
    }
    return count;
```

**if a string is in another string**
```c++
return s0.find(s1)!=string::npos;
```

![image](https://user-images.githubusercontent.com/37808313/115097242-f9802380-9ef6-11eb-84a0-95647a9b9269.png)
