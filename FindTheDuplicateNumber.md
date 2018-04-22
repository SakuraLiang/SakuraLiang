# 题目
一个长度为 n + 1 的整形数组，其中的数字都在 1 到 n 之间，包括 1 和 n ，可知至少有一个重复的数字存在。假设只有一个数字重复，找出这个重复的数字。

注意：

不能更改数组内容（假设数组是只读的）。
只能使用恒定的额外空间，即要求空间复杂度是 O(1) 。
时间复杂度小于 O(n2)
数组中只有一个数字重复，但它可能不止一次重复出现。
# 解法
```ruby
class Solution {
public:
    int findDuplicate(vector<int>&nums) {
    int low=1,high=nums.size()-1;
    while(low<high)
    {
        int cnt=0;
        int mid=(low+high)/2;
        for(int i=0;i<nums.size();i++)
        {
            if(nums[i]<=mid)
                cnt++;
        }
        if(cnt>mid)
        {
            high=mid;
        }
        else
            low=mid+1;
    }
    return low;   
    }
};
```
# 分析
用了二分法，先确定重复的数是在哪个区间，再更改上下限，不断缩小区间。
