# 题目
找出一个序列中乘积最大的连续子序列（该序列至少包含一个数）。

例如， 给定序列 [2,3,-2,4]，
其中乘积最大的子序列为 [2,3] 其乘积为 6。

# 解法

```ruby
class Solution {  
public:  
    int maxProduct(vector<int>& nums) {  
        if(nums.empty())  
        return 0;  
        int maxMul=nums[0];  
        int minMul=nums[0];  
        int ans=nums[0];  
        for(int i=1;i<nums.size();i++)  
        {  
            int a = maxMul*nums[i];    
            int b = minMul*nums[i];    
            maxMul=max(max(a,b),nums[i]);  
            minMul=min(min(a,b),nums[i]);  
            ans=max(ans,maxMul);  
        }  
        return ans;  
    }  
};  

```

# 分析
此题的解题思路是，累乘，将每一次的乘积与第i位的元素相比较，如果乘积小于当前数，则将当前数作为新的起点。但如果前面的累乘是一个负数，而恰好这个数也是一个负数，则不能这样直接处理。之前我自己写出来的代码便没有考虑到这个问题。
为了解决这个问题，需要再定义一个保存最大整数和最小负数的数组。在比较的时候，也要纳入比较范围。
