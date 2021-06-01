# Table of Contents
1. [Vector Initialization](#vector-initialization)
1. [Stack](#stack)
1. [Queue](#queue)
1. [Unordered Map](#unordered-map)
1. [set](#set)
1. [DFS](#dfs)
1. [BFS](#bfs)
1. [Priority Queue](#priority-queue)

## Vector Initialization
```C++
vector<int> vect;
vect.push_back(10);
vect.push_back(20);
vect.push_back(30);

// Create a vector of size n with
// all values as 10.
vector<int> vect(n, 10);

vector<int> vect{ 10, 20, 30 };

vector<vector<int>> twoDVector (n, vector<int> (n, 10)); // n by n, all values as 10
```
### Sort
```C++
sort(s.begin(), s.end(), greater<int>()); // 4321 
sort(s.rbegin(), s.rend()); // 4321
sort(s.begin(), s.end()); // 1234

sort(costs.begin() , costs.end() , [](vector<int>& a,vector<int>& b) -> bool{  // sort by difference between v[1]-v[0] largest to smallest
   return a[1]-a[0] > b[1]-b[0];
});
```
## Stack
- [inorder traversal](https://github.com/liulanz/template/blob/main/tree.md)
```C++
stack<int> stack;
stack.push(21);
stack.push(22);
stack.push(24);
stack.push(25);

stack.pop();
stack.pop();

while (!stack.empty()) {
    cout << ' ' << stack.top(); 
    stack.pop();
}
// 22 21
```
#### Problem
- [20. Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)
## Queue
- [BFS](#bfs)
```C++
queue<int> gquiz;
gquiz.push(10);
gquiz.push(20);
gquiz.push(30);
cout << "\ngquiz.size() : " << gquiz.size(); // gquiz.size() : 3
cout << "\ngquiz.front() : " << gquiz.front(); // gquiz.front() : 10
gquiz.pop();
```
#### Problem
## Unordered Map
```c++
// Declaring umap to be of <string, int> type
// key will be of string type and mapped value will
// be of int type
unordered_map<string, int> umap;

// inserting values by using [] operator
umap["GeeksforGeeks"] = 10;
umap["Practice"] = 20;
umap["Contribute"] = 30;

// Traversing an unordered map
for (auto x : umap)
  cout << x.first << " " << x.second << endl;
  
  
string key = "PI";
// If key not found in map iterator to end is returned
if (umap.find(key) == umap.end())
    cout << key << " not found\n\n";
    
// If key found then iterator to that key is returned
if (umap.find(key) != umap.end())
     cout << "Found " << key << "\n\n";
```
#### Problem
- [389. Find the Difference](https://leetcode.com/problems/find-the-difference/)
- [409. Longest Palindrome](https://leetcode.com/problems/longest-palindrome/)
- [387. First Unique Character in a String](https://leetcode.com/problems/first-unique-character-in-a-string/)
## Set
```c++
// empty set container
set<int> s1;
s1.insert(40);
s1.insert(30);
s1.insert(60);
s1.insert(20);
s1.insert(50);
// only one 50 will be added to the set
s1.insert(50);
s1.insert(10);
 
s1.size(); // get size

if(s1.empty()) // check is empty

s1.erase(40); // remove 40 from set
```
#### Problem
- [217. Contains Duplicate](https://leetcode.com/problems/contains-duplicate/)
- [242. Valid Anagram](https://leetcode.com/problems/valid-anagram/)
- [349. Intersection of Two Arrays](https://leetcode.com/problems/intersection-of-two-arrays/)
## Priority Queue
```C++
priority_queue<int> pq; // 4321 largest to smallest by default
priority_queue<int, vector<int>, greater<int>> pq; // 1234 

auto comp = []( pair<int,int>  a, pair<int,int>  b) { return a.second > b.second; };
priority_queue< pair<int,int> , vector<pair<int,int>>, decltype(comp) > pq( comp );
```

## BFS 
- Use queue
### Tree (Traversal by level)
```C++
vector<vector<int>> res;
if(root==nullptr) return res;
queue<TreeNode*> q;
q.push(root);
while(!q.empty()){
    int sizz = q.size();
    vector<int> tmp;
    for(int i = 0; i <sizz; i++){
        TreeNode* current  = q.front();
        q.pop();
        tmp.push_back(current->val);
        if(current->left != nullptr) q.push(current->left);
        if(current->right != nullptr) q.push(current->right);

    }
    res.push_back(tmp);
}
return res;
```
#### Problem
- [102. Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/)
### 2D Matrix
```C++
// push new, unvisited, valid {row, col, level} to queue
void bfs( queue<vector<int>> &q,vector<vector<int>>& grid, int row, int col, int day){
    if(row <0||col <0||row>=grid.size()||col >=grid[0].size())return;
    if(grid[row][col]==2) return;
    if(grid[row][col]==0) return;
    grid[row][col]=2;
    q.push({row,col,day});
}

int orangesRotting(vector<vector<int>>& grid) {
    if(grid.size()==0) return 0;
    queue<vector<int>> q;
    vector<vector<int>>visited(grid.size(), vector<int>(grid[0].size()));
    for(int row = 0; row <grid.size();row++){
        for(int col = 0; col <grid[0].size();col++){
            if(grid[row][col] ==2){
                q.push({row, col,0});
            }
        }
    }
    int res = 0;
    while(!q.empty()){
        int sizz = q.size();
        for(int i =0; i <sizz;i++){
            vector<int> top = q.front();
            q.pop();
            int r = top[0];
            int c=top[1];
            int day = top[2];
            res=max(res, day);
            // push new, unvisited, valid {row, col, level} to queue
            bfs(q, grid, r+1, c, day+1);
            bfs(q, grid, r-1, c, day+1);
            bfs(q, grid, r, c+1, day+1);
            bfs(q, grid, r, c-1, day+1);
        }
    }
    for(int row = 0; row <grid.size();row++){
        for(int col = 0; col <grid[0].size();col++){
            if(grid[row][col]==1){
                return -1;
            }
        }
    }
    return res;
}

```
#### Problem
- [994 Rotting Oranges](https://leetcode.com/problems/rotting-oranges/)
## DFS
### 1D Back Tracking
```C++
vector<vector<int>> result;
void dfs(vector<int>dup,vector<int>& nums, int i ){
    if(i >=nums.size()){
        result.push_back(dup);
        return;
    }
    // back tracking
    dfs(dup, nums, i+1); // call when excluding
    dup.push_back(nums[i]); //including
    dfs(dup, nums, i+1); // call after including
}
```

#### Problem
- [78. Subsets](https://leetcode.com/problems/subsets/)
- [79. Word Search](https://leetcode.com/problems/word-search/)
### 2D Matrix

```C++
void dfs(vector<vector<int>>& matrix, vector<vector<int>>& visited, int row, int col  ){
    if(row<0||row>=matrix.size()||col <0||col>=matrix[0].size()) return;
    if(visited[row][col]) return;
    if(matrix[row][col]==0) return;
    visited[row][col] = 1;  // keep track of visited cell
    /* 
        do sth in dfs
    */
    dfs(matrix, visited, row+1, col);
    dfs(matrix, visited, row-1, col);
    dfs(matrix, visited, row, col+1);
    dfs(matrix, visited, row, col-1);
}

```
#### Problem
- [200. Number of Islands](https://leetcode.com/problems/number-of-islands/)


