# 题目
在《英雄联盟》的世界中，有一个叫“提莫”的英雄，他的攻击可以让敌方英雄艾希（编者注：寒冰射手）进入中毒状态。现在，给出提莫对艾希的攻击时间序列和提莫攻击的中毒持续时间，你需要输出艾希的中毒状态总时长。

你可以认为提莫在给定的时间点进行攻击，并立即使艾希处于中毒状态。
# 解法（自己写的超时版)

```ruby
class Solution {
public:
    int findPoisonedDuration(vector<int>& timeSeries, int duration) {
        int len=timeSeries.size();
        if(len==0||duration==0) return 0;
        int time=0;
        int flag=timeSeries[0]+duration-1;
        time=duration;
         for(int i=1;i<len;i++)
         {
          for(int j=0;j<duration;j++)
          {
              if(flag<timeSeries[i]+j) 
              
              { 
                  time++;
                  flag=timeSeries[i]+j;
              }
          }
        }
        return time;
    }
};

```
# 分析
题外话 :）港真，英雄联盟这个游戏里面，提莫作为班德尔城的斥候队长，算是我挺喜欢的英雄了，看到这样一道题，真的很迫切想要做出来啊，但是题目其实有不完整的地方，提莫到了最高级，毒液持续时间也只有5秒...
正经话，做这道题我的思路是，用一个flag来表示毒液持续到的时间，第一次放的毒是可以一直持续的，flag直接到第一次放毒完的时间，之后的用两个for循环，第一个大的用来使时间数组的数循环完，第二个用来判断每一次放毒，毒液持续到多久，并计时，并使flag移动。具体做法是，判断flag是否小于数组里的时间依次加到时间+duration。
# 网上的版本
```ruby
class Solution {
public:
    int findPoisonedDuration(vector<int>& timeSeries, int duration) {
        int result = 0, oldEnd = -1;
        for (int i = 0; i < timeSeries.size(); i++) {
            int newEnd = timeSeries[i] + duration - 1;
            if (newEnd > oldEnd) {
                result += min(duration, newEnd - oldEnd);
                oldEnd = newEnd;
            }
        }
        return result;
    }
};
```
# 分析
做法是，把下一次中毒结束的时间与上一次中毒结束的时间对比，如果前者较小或者相等，那此次攻击无效，如果前者较大，那么这次攻击有效的时间就是他们差值，只需进行累加即可。与我的相比，好在没有一秒一秒去比较，而是直接累加。
# 自己的加强版（能通过）

```ruby
class Solution {
public:
    int findPoisonedDuration(vector<int>& timeSeries, int duration) {
        int len=timeSeries.size();
        if(len==0||duration==0) return 0;
        int time=0;
        int flag=timeSeries[0]+duration-1;
        time=duration;
         for(int i=1;i<len-1;i++)
         {
          for(int j=0;j<duration;j++)
          {
              if(flag<timeSeries[i]+j) 
              
              { 
                  time++;
                  flag=timeSeries[i]+j;
              }
          }
        }
        return time+duration;
    }
};

```
# 分析
在看网上另一种解法的时候收到的启发，将最后一次放毒不考虑进循环，因为最后一次也是一定会持续下去的，最后在返回的时候加上duration即可。
