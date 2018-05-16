# 题目
给定一个数组 nums 和一个值 val，你需要原地移除所有数值等于 val 的元素，返回移除后数组的新长度。

不要使用额外的数组空间，你必须在原地修改输入数组并在使用 O(1) 额外空间的条件下完成。

元素的顺序可以改变。你不需要考虑数组中超出新长度后面的元素。
# 解法
```ruby
class Solution {  
public:  
    int removeElement(vector<int>& nums, int val) {  
        int length = nums.size();  
        int j = 0;  
        for(int i = 0; i<length; i++){  
            if(nums[i] != val)  
                nums[j++] = nums[i];  
        }  
        return j;  
          
    }  
};  
```
# 分析
由于不需要考虑超出长度后的元素，直接让覆盖要移出的元素即可。
# 题目
给定一个排序数组，你需要在原地删除重复出现的元素，使得每个元素只出现一次，返回移除后数组的新长度。

不要使用额外的数组空间，你必须在原地修改输入数组并在使用 O(1) 额外空间的条件下完成。
# 解法
```ruby
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        int len=nums.size();
        if(len==0) return 0;
        int result=1;
        for(int i=1;i<len;i++)
        {
         if(nums[i]!=nums[i-1])
         {
             nums[result]=nums[i];
             result++;
         }
        }
        return result;
    }
};
```
# 分析
与上一题类似，判断方法稍作改动。
