```C++ 
int partition(vector<int>& nums, int start, int end) {
    int pivot = nums[start], j = end;
    for (int i = start + 1; i <= j;) {
        if (nums[i] >= pivot)
            swap(nums[i], nums[j--]);
        else
            i++;
    }
    swap(nums[start], nums[j]);
    return j;
}

int solve(vector<int>& nums, int k) {
    int l = 0, r = nums.size() - 1;
    while (l <= r) {
        int m = partition(nums, l, r);
        if (m < k)
            l = m + 1;
        else
            r = m - 1;
    }
    return nums[k];
}
```
