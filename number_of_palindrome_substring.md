## longest palindromic sub sequence 
```c++
int solve(string s) {
    vector<vector<int>> dp(s.length(), vector<int>(s.length()));
    for(int i = 0; i <s.length();i++){
        dp[i][i]  =1;
    }
    int n = s.length();

    for(int k = 2; k <=dp.size();k++){
    for(int i = 0; i <s.length()-k+1;i++){
        
        int j = i+k-1;
            if(s[i]==s[j]){
                dp[i][j] = dp[i+1][j-1]+2;
        
            }
            else{
                dp[i][j]  = max(dp[i+1][j], dp[i][j-1]);
            }
        }
    }
   return  dp[0][n-1]; 
     return n-dp[0][n-1];   // # of  insert  to make it into substring
}
```

## number of palindrome_substring

#### only use upper right of 2d vectors, must fill first two diagonals first
![Screenshot 2021-05-03 195506](https://user-images.githubusercontent.com/37808313/116947841-ca361a00-ac4b-11eb-8c43-eaac156a73ac.png)
```c++
int solve(string s) {
    int count = 0;
    vector<vector<bool>> dp(s.length(), vector<bool>(s.length(), false));

    int res = 0;
    for(int row = 0; row <dp.size();row++){
        dp[row][row] = true;
        res++;
    }
    for(int row =0; row<dp.size()-1;row++){
        if(s[row]==s[row+1]){
            dp[row][row+1] = true;
            res++;
        }
        
    }
  int n = dp.size(); 
        // Check for lengths greater than 2.
        // k is length of substring
    for (int k = 3; k <= n; ++k) {   // *** <=n ***
                 // starting index i
        for (int i = 0; i < n - k + 1; ++i) {  
                // Get the ending index of substring from
                // starting index i and length k
            int j = i + k - 1;
 
            if(s[i]==s[j] && dp[i+1][j-1]){
                dp[i][j] = true;
                res++;
            }
        }
        
    }
  
    return res;
}
```


---

## O(1) Space

```c++
int numberPalindrome(int l, int r, string s){
    if(l>r ||s=="") return 0;
    int res = 0;
    while(l>=0 && r <s.length() && s[l]==s[r]){
        l--;
        res++;
        r++;
    }
    return res;
}
int solve(string s) {
    int res = 0;
    for(int i = 0; i <s.length();i++){
        int l = numberPalindrome(i, i, s);
        int r = numberPalindrome(i, i+1, s);
        res+= l+r;
    }
    return res;
}
```
