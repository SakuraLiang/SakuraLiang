# 题目
给定一个长度为 n 的整数数组，你的任务是判断在最多改变 1 个元素的情况下，该数组能否变成一个非递减数列。

我们是这样定义一个非递减数列的： 对于数组中所有的 i (1 <= i < n)，满足 array[i] <= array[i + 1]。
# 解法
```ruby
class Solution {  
public:  
  
    bool checkPossibility(vector<int>& nums) {  
        int cnt = 0;  
        for(int i = 1; i < nums.size() && cnt <=1; i++){  
            if(nums[i-1] > nums[i]){  
                cnt++;  
                if(i-2 < 0 || nums[i-2] <= nums[i])  
                    nums[i-1] = nums[i];  
                else  
                    nums[i] = nums[i-1];  
            }  
        }  
        return cnt <= 1;  
    }  
};  
```
# 分析
一旦出现后一个数比前一个数小，就需要一个数。改变数可以有两种方式，一种是，较大的数是第二个时或者较大的数是第二个之后的，且较大数的前一个小于较大数的后一个，就可将较大数改为跟前一个一样的。除此之外，为了尽量满足规律，只能将较小数改为跟较大数一样。



p:6505
