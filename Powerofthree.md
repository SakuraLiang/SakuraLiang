# 题目
Given an integer, write a function to determine if it is a power of three.

Follow up:
Could you do it without using any loop / recursion?
# 解法

```ruby
class Solution {
public:
        bool isPowerOfThree(int n){
    if(n==1)  return true;
    else if(n==0)  return false;
    else if(n%3==0)
    return isPowerOfThree(n/3);
    else return false;
    }
};

```
# 分析
可以采用递归的方法，先判断数是不是1，是直接返回true，再判断这个数是不是0，如果是直接返回false，再判断这个数能否被3整除，如果不能，直接返回false，如果能，将这个数除以3再执行整个函数。如果是3的幂，最后便一定会变成1.
# 不用递归

```ruby
class Solution {
public:
    bool isPowerOfThree(int n) {
        double logAns = log10(n) / log10(3);
        return (logAns - int(logAns) == 0) ? true : false;
    }
};

```
# 分析
判断double型的log3(n)是否与int型的log3(n)相等，如果相等，便是3的幂。这种思路在其他地方也可以用上。
