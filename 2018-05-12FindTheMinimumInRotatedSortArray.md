# 题目
假设按照升序排序的数组在预先未知的某个点上进行了旋转。

( 例如，数组 [0,1,2,4,5,6,7] 可能变为 [4,5,6,7,0,1,2] )。

请找出其中最小的元素。

你可以假设数组中不存在重复元素。
# 解法(4ms)
```ruby
class Solution {
public:
    int findMin(vector<int>& nums) {
        int len=nums.size();
        int result=nums[0];
        for(int i=0;i<len;i++)
        {
            if(nums[i]<result)
                result=nums[i];
        }
        return result;
    }
};
```
# 分析
进行一次循环，找出最小值即可。
# 题目
假设按照升序排序的数组在预先未知的某个点上进行了旋转。

( 例如，数组 [0,1,2,4,5,6,7] 可能变为 [4,5,6,7,0,1,2] )。

请找出其中最小的元素。

注意数组中可能存在重复的元素。
# 解法(4ms)
```ruby
class Solution {
public:
    int findMin(vector<int>& nums) {
        int result=nums[0];
        for(int i=0;i<nums.size()-1;i++)
        {
            if(nums[i]>nums[i+1])
                result=nums[i+1];
        }
        result=min(result,nums[nums.size()-1]);
        return result;
    }
};
```
# 分析
找出后一个数比前一个数大的情况，即是数组起点。再排除起点旋转到最后的情况。
