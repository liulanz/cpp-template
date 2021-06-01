# Table of Contents
1. [Vector Initialization](#vector-initialization)
1. [Stack](#stack)
1. [Queue](#queue)
1. [BFS](#bfs)
1. [Unordered Map](#unordered-map)
1. [set](#set)

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
```

## Stack
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
## BFS 
- Use queue
### Tree (Traversal by level)
- [102. Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/)
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


