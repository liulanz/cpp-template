```C++ 
// Standard partition process of QuickSort().
// It considers the last element as pivot
// and moves all smaller element to left of
// it and greater elements to right
int partition(vector<int>& nums, int l, int r)
{
    int pivot = nums[r], i = l;
    for (int j = l; j <= r - 1; j++) {
        if (nums[j] <= pivot) {
            swap(nums[i], nums[j]);
            i++;
        }
    }
    swap(nums[i], nums[r]);
    return i;
}

int solve(vector<int>& nums, int k) {
    int l = 0, r = nums.size() - 1;
    while (l < r) {
        int m = partition(nums, l, r);
        if (m == k)             //quick select 
            return nums[m];     
            
        else if (m < k)
            l = m + 1;
        else
            r = m - 1;
    }
    return nums[k];
}
```

O(N) for quick select, 
O(NlogN) quick sort
