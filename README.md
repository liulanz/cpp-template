# template


**number of sublist**: ``res += (1+cnt)*cnt/2``

**priority_queue**: ``(<: 4321, >: 1234)`` <br/>
```c++ 
priority_queue<int, vector<int>, greater<int>> pq; // 1234
```
```c++
auto comp = []( pair<int,int>  a, pair<int,int>  b) { return a.second > b.second; };
priority_queue< pair<int,int> , vector<pair<int,int>>, decltype(comp) > pq( comp );
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
 
