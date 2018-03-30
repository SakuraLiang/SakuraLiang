## 题目
实现 pow(x, n)。
# 解法

```ruby
class Solution {
public:
    double myPow(double x, int n) {
        if(n==0) return 1;
        double sum=1;
      if(n>0){  while(n>0){
            sum=sum*x;
            n--;
        }}
    if(n<0){n=-n;
           while(n>0){
               sum=sum*x;
               n--;
           }
           sum=1/sum;}
    return sum;}
};

```
# 分析
自己的写法，仍然是小数据能通过大数据便会超时。
# 解法2

```ruby
double pow(double x, int n)  
{  
    if(n==0)  
        return 1.0;  
    if(n<0)  
        return 1.0/pow(x,-n);  
    return x*pow(x,n-1);  
}

```
# 分析
网上的方法，用到了递归。值得借鉴
