# 题目
给定一个整数数组 a，其中1 ≤ a[i] ≤ n （n为数组长度）, 其中有些元素出现两次而其他元素出现一次。

找到所有出现两次的元素。

你可以不用到任何额外空间并在O(n)时间复杂度内解决这个问题吗？
# 解法
```ruby
class Solution {
public:
    vector<int> findDuplicates(vector<int>& nums) {
        vector<int>array;
        int len=nums.size();
        for(int i=0;i<len;i++)
        {
          int clue=abs(nums[i])-1;
            if(nums[clue]<0)
            {
                array.push_back(clue+1);
            }
            nums[clue]=-1*nums[clue];
        }
        return array;
    }
};

```
# 分析
还是利用数组下标，每一次都对相应位置上的数置为相反数，在执行置相反数之前，先判断那个数是否已经被置为相反数过，如果是，那个数就会是负的，一旦是，就把那个数位+1的数加入动态数组。
