# 题目

给定一个数组 nums, 编写一个函数将所有 0 移动到它的末尾，同时保持非零元素的相对顺序。

例如， 定义 nums = [0, 1, 0, 3, 12]，调用函数之后， nums 应为 [1, 3, 12, 0, 0]。

# 解法

```ruby
class Solution {
public:
    void moveZeroes(vector<int>& nums)   {
        int len = nums.size();  
        int k = 0;  
        for(int i = 0; i < len; i ++)  
        {  
            if(nums[i]) {  
                nums[k ++] = nums[i];  
            }  
        }  
        for(int i = k; i < len; i ++)  
            nums[i] = 0;  
    }  
};

```

# 分析
因为是将0移到数组最后，换个角度理解就是把非0元素排在前面，之后的元素全部令为0，因此，可以设置一个标记变量k，k的初始值为0，进行遍历，当此次的元素不为0时，就把它赋给数组的第k位，k累加。遍历完成之后，从k开始以后的元素都是0.因此只需在进行一个从k开始的循环，赋值为0即可。
