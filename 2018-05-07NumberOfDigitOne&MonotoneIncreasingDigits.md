# 题目
给定一个二进制数组， 计算其中最大连续1的个数
# 解法
```ruby
class Solution {
public:
    int findMaxConsecutiveOnes(vector<int>& nums) {
        int len=nums.size();
        int sum=0,temp=0;
        for(int i=0;i<len;i++)
        {
            if(nums[i]==1)
            {
                temp++;
            }
            sum=max(temp,sum);
            if(nums[i]==0)
            {
                temp=0;
            }
        }
        return sum;
    }
};
```
# 分析
一开始写的时候还是有很多细节没有注意。后来想了一下，用每出现一个1就比较一次临时储存数量的值和最后将返回的值，取较大者，这样做最为方便。
# 题目
给定一个非负整数 N，找出小于或等于 N 的最大的整数，同时这个整数需要满足其各个位数上的数字是单调递增。

（当且仅当每个相邻位数上的数字 x 和 y 满足 x <= y 时，我们称这个整数是单调递增的。）
# 解法
```ruby
class Solution {
  public:
    int monotoneIncreasingDigits(int N)
    {
        string n_str = to_string(N);
        int marker = n_str.size();
        for (int i = n_str.size() - 1; i > 0; i--)
        {
            if (n_str[i] < n_str[i - 1])
            {
                marker = i;
                n_str[i - 1] = n_str[i - 1] - 1;
            }
        }

        for (int i = marker; i < n_str.size(); i++)
            n_str[i] = '9';

        return stoi(n_str);
    }
};
```
# 分析
网上的代码。利用字符串数组相互转换的函数，将其变成对字符串的处理。
