# 题目
给定一个范围在  1 ≤ a[i] ≤ n ( n = 数组大小 ) 的 整型数组，数组中的元素一些出现了两次，另一些只出现一次。

找到所有在 [1, n] 范围之间没有出现在数组中的数字。

您能在不使用额外空间且时间复杂度为O(n)的情况下完成这个任务吗? 你可以假定返回的数组不算在额外空间内。
# 解法
```ruby
class Solution {
public:
    vector<int> findDisappearedNumbers(vector<int>& nums) {
        vector<int>array;
        int len=nums.size();
        for(int i=0;i<len;i++)
        {
           int clue=abs(nums[i])-1;
            if(nums[clue]>0)
            {
                nums[clue]=-1*nums[clue];
            }
        }
        for(int i=0;i<len;i++)
        {
            if(nums[i]>0)
            {
                array.push_back(i+1);
            }
        }
        return array;
    }
};
```
# 分析
利用数组的下标来标记，把对应位置的元素的值置为相反数，注意开始时绝对值符号的添加。
