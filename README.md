# template


**number of sublist**: ``res += (1+cnt)*cnt/2``

**priority_queue**:
```c++
auto comp = []( pair<int,int>  a, pair<int,int>  b) { return a.second > b.second; };
priority_queue< pair<int,int> , vector<pair<int,int>>, decltype(comp) > pq( comp );
```
