## number of palindrome_substring

#### only use upper right of 2d vectors, must fill first two diagonals first

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

