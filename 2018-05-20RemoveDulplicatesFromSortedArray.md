# 题目

给定一个排序数组，你需要在原地删除重复出现的元素，使得每个元素最多出现两次，返回移除后数组的新长度。

不要使用额外的数组空间，你必须在原地修改输入数组并在使用 O(1) 额外空间的条件下完成。
# 解法
```ruby
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        int n=nums.size();
        if(n < 3)
            return n;
        int index = 2;
        for(int i = 2; i < n; i ++)
        {
            if(nums[i] != nums[index-2])
                nums[index ++] = nums[i];
        }
        return index;
    }
};
```
# 分析
用index记录新数组的下标。用i去遍历原来的数组。
