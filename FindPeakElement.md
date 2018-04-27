# 题目
峰值元素是指其值大于左右相邻值的元素。

给定一个输入数组 nums，其中 num[i] ≠ num[i+1]，找到峰值元素并返回其索引。

数组可能包含多个峰值，在这种情况下，返回到任何一个峰值所在位置都可以。

你可以假设 num[-1] = num[n] = -∞。
# 解法
```ruby
class Solution {
public:
    int findPeakElement(vector<int>& nums) {  
        int left=0,right=nums.size()-1;  
        while (left<right) {  
            int mid=(left+right)/2;  
            if(nums[mid]<nums[mid+1])
                left=mid+1;  
            else right = mid;  
        }  
        return left;    
        
    }
};
```
# 分析
根据题意，一定会有一个峰值。用二分法，不断改变上下限，当上下限相遇时，所在的位置即是峰值。
