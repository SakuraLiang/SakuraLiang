# 题目
给定一个包含红色、白色和蓝色，一共 n 个元素的数组，原地对它们进行排序，使得相同颜色的元素相邻，并按照红色、白色、蓝色顺序排列。

此题中，我们使用整数 0、 1 和 2 分别表示红色、白色和蓝色。
# 解法
```ruby
class Solution {
public:
    void sortColors(vector<int>& nums) {
        int n0=0;
        int n1=0;
        int n2=0;
        for(int i=0;i<nums.size();i++)
        {
            if(nums[i]==0) n0++;
            if(nums[i]==1) n1++;
            if(nums[i]==2) n2++;
        }
        for(int i=0;i<n0+n1+n2;i++)
        {
         if(i<n0) nums[i]=0;
         if(i>=n0&&i<n1+n0) nums[i]=1;
         if(i>=n0+n1) nums[i]=2;
        }
    }
};
```
# 分析
对每个数字出现的次数进行计数，遍历一遍根据计数来更改每个位置的值。
