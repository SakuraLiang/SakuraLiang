# 题目
在一条环路上有 N 个加油站，其中第 i 个加油站有汽油 gas[i] 升。

你有一辆油箱容量无限的的汽车，从第 i 个加油站开往第 i+1 个加油站需要消耗汽油 cost[i] 升。你从其中的一个加油站出发，开始时油箱为空。

如果你可以绕环路行驶一周，则返回出发时加油站的编号，否则返回 -1。
# 解法
```ruby
class Solution {
public:
    int canCompleteCircuit(vector<int>& gas, vector<int>& cost) {
    int start=0;
   int remain=0;
    int debt=0;
      for(int i=0;i<gas.size();i++) {
      remain+=gas[i]-cost[i];
      if (remain<0) {
        debt+=remain;
       start=i+1;
       remain=0;
     }
   }
    return remain+debt>=0?start:-1;
    }
};
```
# 分析
因为如果要环绕一圈，那么所有得到的汽油一定要比消耗的汽油多。所以遍历一圈，把最后剩余的汽油算出来，如果小于0了，就不能环绕一圈。
