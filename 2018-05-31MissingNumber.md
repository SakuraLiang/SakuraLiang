# 题目

给定一个包含 0, 1, 2, ..., n 中 n 个数的序列，找出 0 .. n 中没有出现在序列中的那个数。
# 解法
```ruby
class Solution {
public:
    int missingNumber(vector<int>& nums) {
        int len=nums.size();
        int sum=len*(len+1)/2;
        for(int i=0;i<len;i++)
        {
            sum-=nums[i];
        }
        return sum;
    }
};
```
# 分析
先将不缺失数字时的数列累加，再遍历一遍减掉，得到的即为缺失的。
# 解法2
```ruby
class Solution {
public:
    int missingNumber(vector<int>& nums) {
        int len=nums.size();
        int result=len;
        for(int i=0;i<len;i++)
        {
            result^=i;
            result^=nums[i];
        }
        return result;
    }
};
```
# 分析
利用异或。异或两次同一个数就会得到原来那个数。将出现过的数异或一次，将0~n异或一次。
