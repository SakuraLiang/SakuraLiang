# 题目
给定一个整型数组，在数组中找出由三个数组成的最大乘积，并输出这个乘积。
# 解法

```ruby
class Solution {
public:
    int maximumProduct(vector<int>& nums) {
        sort(nums.begin(),nums.end());
        int n=nums.size();
        int s=nums[n-1]*nums[n-2]*nums[n-3];
        if(s<nums[n-2]*nums[n-1]*nums[0]) s= nums[n-2]*nums[n-1]*nums[0];
        if(s<nums[0]*nums[1]*nums[n-1]) s=nums[0]*nums[1]*nums[n-1];
        if(s<nums[0]*nums[n-1]*nums[n-2]) s=nums[0]*nums[n-1]*nums[n-2];
        return s;
        
    }
};

```
# 分析
解决此题的方法是，将数组先排序，此时，最大值的情况只可能有四种，一是后三个数的乘积最大，一种是最后一个数和前两个数乘积最大，一种是前三个数乘积最大，还有一种是后两个数和第一个数乘积最大，只需要比较后返回其中的最大值即可。涉及到最大最小的时候，可以多考虑考虑先排序再解决。
