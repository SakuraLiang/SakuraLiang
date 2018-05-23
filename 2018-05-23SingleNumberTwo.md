# 题目
给定一个非空整数数组，除了某个元素只出现一次以外，其余每个元素均出现两次。找出那个只出现了一次的元素。
# 解法
```ruby
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        int result=0;
     for(int i=0;i<nums.size();i++)
     {
         result^=nums[i];
     }
        return result;
    }
};
```
# 分析
异或的应用，一开始没想到，看了网上的恍然大悟。两个等的数异或为0,0与任意一个数异或等于那个数本身。
