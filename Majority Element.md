# 题目
给定一个大小为 n 的数组，找到其中的众数。众数是指在数组中出现次数大于 ⌊ n/2 ⌋ 的元素。

你可以假设数组是非空的，并且数组中的众数永远存在。

# 解法1

```ruby
class Solution {
public:
     int majorityElement(vector<int>& nums) {
            if(nums.size()==1)
                return nums[0];
            map<int,int> tables;
            for(int i=0;i<nums.size();i++)
            {
                if(tables.count(nums[i]))
                {
                    tables[nums[i]]++;
                    if(tables[nums[i]]>nums.size()/2)
                        return nums[i];
                }
                else
                {
                    tables[nums[i]]=1;
                }
            }


     }
};

```

# 分析
这种解法利用的是哈希表，一旦数字出现过，就累加一次，没有出现过，便插入哈希表，从1开始，每判断一个元素，也要看这个元素的是否超过总元素的二分之一，一旦超过，便返回这个值。我在想这种方法的时候，并没有考虑到每个元素累加之后都判断一次是否大于元素个数的二分之一，而是想在最后寻找次数大于总元素二分之一的。此外，哈希表的准确使用方法也有待学习。

# 解法2

```ruby
class Solution {
public:
      int majorityElement(vector<int>& nums) {
        sort(nums.begin(),nums.end());
        return nums[nums.size()/2];
    }
};

```
# 分析
这种方法就更厉害了。先进行排序，只要是众数，就一定会出现在中间。只要返回中间值即可。
