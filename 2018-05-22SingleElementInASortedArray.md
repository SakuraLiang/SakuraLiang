# 题目
给定一个只包含整数的有序数组，每个元素都会出现两次，唯有一个数只会出现一次，找出这个数。
注意: 您的方案应该在 O(log n)时间复杂度和 O(1)空间复杂度中运行。
# 解法
```ruby
class Solution {
public:
    int singleNonDuplicate(vector<int>& nums) {
        int len=nums.size();
        if(len==1) return nums[0];
        if(nums[1]!=nums[0]) return nums[0];
        for(int i=1;i<nums.size()-1;i++)
        {
            if(nums[i]!=nums[i-1]&&nums[i]!=nums[i+1])
                return nums[i];
        }
        return nums[len-1];
    }
};
```
# 分析
这种方法没有达到时间复杂度和空间复杂度的要求。
```ruby
class Solution {
public:
    int singleNonDuplicate(vector<int>& nums) {
        int left=0,right=nums.size()-1;
        while (left <= right) {
            int mid = (left + right) / 2;
            if (mid != 0 && mid != nums.size() - 1) {
                if (nums[mid - 1] == nums[mid]) {
                    if (mid % 2 == 0) {
                        right = mid - 2;
                    }
                    else {
                        left = mid + 1;
                    }
                }
                else if (nums[mid] == nums[mid + 1]) {
                    if (mid % 2 == 0) {
                        left = mid + 2;
                    }
                    else {
                        right = mid - 1;
                    }
                }
                else {
                    return nums[mid];
                }
            }
            else if (mid == 0) {
                if (nums[0] == nums[1]) {
                    left = 2;
                }
                else {
                    return nums[0];
                }
            }
            else if (mid == nums.size() - 1) {
                if (nums[nums.size() - 2] == nums[nums.size() - 1]) {
                    right = nums.size() - 3;
                }
                else {
                    return nums[nums.size() - 1];
                }
            }
        }
    }
};
```
# 分析
二分法。
