# 题目
给定一个包括 n 个整数的数组 nums 和 一个目标值 target。找出 nums 中的三个整数，使得它们的和与 target 最接近。返回这三个数的和。假定每组输入只存在唯一答案。
# 解法
```ruby
class Solution {
public:
    int threeSumClosest(vector<int>& nums, int target) {
        int closest=nums[0]+nums[1]+nums[2];
        int diff=abs(closest-target);
        sort(nums.begin(),nums.end());
        for (int i=0;i<nums.size()-2;i++)
        {
            int start=i+1;
            int end=nums.size()-1;
            while (start<end) {
                int sum=nums[i]+nums[start]+nums[end];
                int newDiff=abs(su-target);
                if (newDiff<diff){
                    diff=newDiff;
                    closest=sum;
                }
                if (sum<target)
                    start++;
                else
                    end--;
            }
        }
        return closest;
    }  
};
```
# 分析
用两个指针和一个循环。从第0为到倒数第二位遍历，每一位上的数，都用两个指针分别遍历剩下的数，如果有更接近的，就替换。
