# 题目

给定一个非负整数 c ，你要判断是否存在两个整数 a 和 b，使得 a2 + b2 = c。
# 解法

```ruby
class Solution {
public:
  bool judgeSquareSum(int c) {  
    int limit = sqrt(c);  
    for(int n=0;n<=limit;n++)  
    {  
        double test=sqrt(c-n*n);  
        if(test-(int)test==0)  
            return true;  
    }  
    return false;  
} 
       
};

```
# 分析
自己写的代码一如既往的数据一大就超时。看了网上的答案，才明白简便的方法。从0开始，到n的平方根结束，依次判断n减去那个数的平方后剩下的数再开根的数是不是整数，如果是，那就是符合题目要求的数，到n的平方根结束，如果一直没有，则不是符合要求的数。我自己在想的时候，没有利用到如果开根成一个double型的数再减去开根成一个整型的数可以判断这个数是不是整数的平方。
