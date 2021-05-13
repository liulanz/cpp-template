```c++
class FenwickTree{
    private:
        vector<int> tree_;
    public:
        FenwickTree(int n){
            tree_ = vector<int>(n+1,0);
        }
        void update(int i, int diff){
            while(i <tree_.size()){
                tree_[i]+=diff;
                i += i&(-i);
            }
            
        }
        int query(int i){
            int sum = 0;
            while(i>0){
                sum+=tree_[i];
                i-= i&(-i);
            }
            return sum;
        }
};
class NumArray {
public:
    
    NumArray(vector<int>& nums):tree_(nums.size()){

        nums_=nums;
        for(int i = 0; i <nums.size();i++){
            tree_.update(i+1, nums[i]);
        }
    }
    
    void update(int index, int val) {
        tree_.update(index+1,val -nums_[index]);
        nums_[index]=val;
    }
    
    int sumRange(int left, int right) {
        return tree_.query(right+1)-tree_.query(left);
        
    }
private:
    FenwickTree tree_;
    vector<int> nums_;
};

/**
 * Your NumArray object will be instantiated and called as such:
 * NumArray* obj = new NumArray(nums);
 * obj->update(index,val);
 * int param_2 = obj->sumRange(left,right);
 */
```
![tree](https://user-images.githubusercontent.com/37808313/118169551-107f3c00-b3f7-11eb-8e51-de4b4d29add7.png)
