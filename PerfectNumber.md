# 题目
对于一个 正整数，如果它和除了它自身以外的所有正因子之和相等，我们称它为“完美数”。

给定一个 正整数 n， 如果他是完美数，返回 True，否则返回 False
# 解法
1
```ruby
class Solution {
public:
    bool checkPerfectNumber(int num) {
        int k=0;
        for(int i=1;i<num;i++){
            if(num%i==0) k=k+i;
            if(k>num) return false;
        }
        if(k==num) return true;
        return false;
    }
};

```
2

```ruby
class Solution {  
public:  
    bool checkPerfectNumber(int num) {  
        if(num==1) return false;  
        int sum=0;  
        for(int i=2;i<sqrt(num);i++)  
        if(num%i==0)  
        {  
            sum+=i;  
            if(i!=num/i) sum+=num/i;  
        }  
        sum++;  
        return sum==num;  
    }  
}; 

```
# 分析
前一个是我自己写的，思路是建立一个循环把所有的正因子累加，并在每一步都判断累加的和是否大于这个数。当数据很大时，便会超时。参考了网上的答案，普遍的做法都是在输入的数的平方根就停止循环，因为在超过了平方数后就不可能还有能整除的数。之前也有类似的问题，一直没有引起过自己的注意。代码不紧要注重是否能算出结果，更要注重效率。
