# 哈希表

当我们遇到了要快速判断一个元素是否出现集合里的时候，就要考虑哈希法。

但是哈希法也是牺牲了空间换取了时间，因为我们要使用额外的数组，set或者是map来存放数据，才能实现快速的查找。

| 集合 | 底层实现 | 是否有序 | 数值是否可以重复 | 能否更改数值 | 查询效率 | 增删效率 |
|---| --- | --- | --- | ---|---|---|
|std::set|红黑树|有序|否|否|O(log n) | O(log n)|
|std::multiset| 红黑树|有序|是|否|O(log n)|O(log n)|
|std::unordered_set|哈希表|无序|否|否|O(1)|O(1)|

| 映射 | 底层实现 | 是否有序 | 数值是否可以重复 | 能否更改数值 | 查询效率 | 增删效率 |
|---| --- | --- | --- | ---|---|---|
|std::map|红黑树|key有序|key不可重复|key不可修改|O(log n) | O(log n)|
|std::multimap| 红黑树|key有序|key可重复|key不可修改|O(log n)|O(log n)|
|std::unordered_map|哈希表|key无序|key不可重复|key不可修改|O(1)|O(1)|

## 双指针法

双指针法解决多数求和 = target 问题：
使用递归法：
```
class Solution {
public:
    vector<vector<int>> nSumTarget(vector<int>& nums, int n, int start, long target){
        int nums_size = nums.size();
        vector<vector<int>> result;
        if(n < 2 || nums_size < n)  return result;
        // base case
        if(n == 2){
            int left = start;
            int right = nums_size - 1;
            while(left < right){
                if(nums[left] + nums[right] > target){
                    right--;
                }
                else if(nums[left] + nums[right] < target){
                    left++;
                }
                else{
                    result.push_back(vector<int>{nums[left], nums[right]});
                    while(left < right && nums[right] == nums[right - 1]) right--;
                    while(left < right && nums[left] == nums[left + 1]) left++;
                    right--;
                    left++;
                }
            }
        }
        else{
            for(int i = start; i < (nums_size - n + 1); i++){
                // 剪枝
                if(nums[i] > target && nums[i + 1] >= 0) break;
                vector<vector<int>> subVec = nSumTarget(nums, n - 1, i + 1, long(target - nums[i]));
                for(vector<int> &arr : subVec){
                    arr.push_back(nums[i]);
                    result.push_back(arr);
                }
                while(i < (nums_size - 1) && nums[i] == nums[i + 1])  i++;
            }
        }
        return result;
    }
    vector<vector<int>> fourSum(vector<int>& nums, int target) {
        sort(nums.begin(), nums.end());
        return nSumTarget(nums, 4, 0, long(target));
    }
};
```
