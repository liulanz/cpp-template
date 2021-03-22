# template


**number of sublist**: ``res += (1+cnt)*cnt/2``

**priority_queue**:
```c++
priority_queue< pair<int,int> , vector<pair<int,int>>,
    [](pair<int,int>  a, pair<int,int>  b) -> bool {
        if(a.first > b.first){ return true; } else { return false; }
    }> pq;
```
