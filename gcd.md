```c++
int gcd(int a, int b){
    if(a==0){
    return b;
    }
    return gcd(b%a, a);
}
int solve(vector<int>& nums) {
   if(nums.size()==0) return -1;
   int res = nums[0];
   for(int i = 1; i <nums.size();i++){
       res = gcd(res, nums[i]);
       if(res ==1) return 1;
   } 
   return res;

}
```
