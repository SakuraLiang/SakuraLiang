# 题目
You are climbing a stair case. It takes n steps to reach to the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

# 解法

```ruby
class Solution {
public:
    int climbStairs(int n){
        if (n<=0)
            return 0;
        else if(n==1)
            return 1;
        else if(n==2)
            return 2;
        int *r=new int[n];
        r[0]=1;
        r[1]=2;
        for (int i=2;i<n;i++)
        r[i]=r[i-1]+r[i-2];
        int ret=r[n-1];
        delete []r;
        return ret;
    }
};

```
# 分析
当阶梯数大于2时，每一阶梯时方法的总数是上一阶梯走一步或上两个阶梯走两步得来的，因此，只需把每一步阶梯的总数存起来，最后返回最后一步的即可。
