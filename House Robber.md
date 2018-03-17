# 题目
You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security system connected and it will automatically contact the police if two adjacent houses were broken into on the same night.

Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight without alerting the police.

# 解法

```ruby
class Solution {
public:
    int rob(vector<int>& nums) {
        int n=nums.size();
        if(n==0) return 0;
        if(n==1) return nums[0];
        else 
        {  vector<int> sum(n,0); int i=2;
        sum[0]=nums[0];
        sum[1]=max(nums[0],nums[1]);
        while(i<n){
                sum[i]=max(sum[i-2]+nums[i],sum[i-1]);
                i++;
            }return sum[i-1];} 
    }
   
};

```

# 分析
动态规划。用百度的话来说，是把多阶段过程转化为一系列单阶段问题，利用各阶段之间的关系，逐个求解，创立了解决这类过程优化问题的新方法。在此题中，在第i家的最大利益只有两种情况，一是i-1家已经偷盗，利益i-1家的利益，二是i-1家未偷盗i-2家偷盗，利益为i-2家加上i家。当i-1家未偷盗，i家也不偷盗，此时的利益与仍未i-1家时的利益。只需在这两种答案中选出最大者作为解即可。最后返回为第i家时的利益。
