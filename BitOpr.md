# 题目
给定一个整数，写一个函数来判断它是否是2的幂。
# 解法
```ruby
class Solution {
public:
    bool isPowerOfTwo(int n) {
        if(n<=0) return false;
        while(n>1)
        {
            if((n-(n>>1)*2)!=0) return false;
            n=n>>1;
        }
        return true;
    }
};
```
# 分析
一直除以2，看能不能被整除，一旦不能，返回false，到最后返回true。
# 题目
给定一个整数 (32位有符整数型)，请写出一个函数来检验它是否是4的幂。
# 解法
```ruby
class Solution {
public:
    bool isPowerOfFour(int num) {
        if(num<=0) return false;
        while(num>1)
        {
            if((num-(num>>2)*4)!=0) return false;
            num=num>>2;
        }
        return true;
    }
};
```
# 分析
与上一题做法类似。
# 题目
给定一个非负整数 num。 对于范围 0 ≤ i ≤ num 中的每个数字 i ，计算其二进制数中的1的数目并将它们作为数组返回。
# 解法
```ruby
class Solution {
public:
    vector<int> countBits(int num) {
     vector<int>result(num+1,0);
    for(int i=1;i<num+1;i++)
     {
         result[i]=result[i>>1]+i%2;
     }
    return result;
    }
};
```
