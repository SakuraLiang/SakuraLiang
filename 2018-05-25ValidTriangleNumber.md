# 题目
给定一个包含非负整数的数组，你的任务是统计其中可以组成三角形三条边的三元组个数。
# 解法(764ms)
```ruby
class Solution {
public:
    int triangleNumber(vector<int>& nums) {
        sort(nums.begin(),nums.end());
        int len=nums.size();
        if(len<=2) return 0;
        int count=0;
        for(int i=0;i<len-2;i++)
        {
            for(int k=i+1;k<len-1;k++)
            {
                 for(int j=k+1;j<len;j++)
                 {
                       if(nums[i]+nums[k]>nums[j])
                       {count++;
                     }
                 }
            }
        }
        return count;
    }
};
```
# 分析
最笨的一种方法。
# (12ms)
```ruby
class Solution {
public:
    int triangleNumber(vector<int>& nums) {
        int res = 0, n = nums.size();
        sort(nums.begin(), nums.end());
        for (int i = n - 1; i >= 2; --i) {
            int left = 0, right = i - 1;
            while (left < right) {
                if (nums[left] + nums[right] > nums[i]) {
                    res += right - left;
                    --right;
                } else {
                    ++left;
                }
            }
        }
        return res;
    }
};
```
# 分析
从大到小先确定第三边，然后把符合条件的区间求出来。
