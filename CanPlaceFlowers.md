# 题目
假设你有一个很长的花坛，一部分地块种植了花，另一部分却没有。可是，花卉不能种植在相邻的地块上，它们会争夺水源，两者都会死去。

给定一个花坛（表示为一个数组包含0和1，其中0表示没种植花，1表示种植了花），和一个数 n 。能否在不打破种植规则的情况下种入 n 朵花？能则返回True，不能则返回False。
# 解法

```ruby
class Solution {
public:
    bool canPlaceFlowers(vector<int>& flowerbed, int n) {
        int len=flowerbed.size();
        if(n==0) return true;
        if(len==1){
            if(flowerbed[0]==0&&n<=1)   return true;
            else return false;} 
        int count=0;
        if(flowerbed[0]==0&&flowerbed[1]==0){ count++;flowerbed[0]=1;if(count==n) return true;}
        for(int i=1;i<len-1;i++){
            if(flowerbed[i-1]==0&&flowerbed[i]==0&&flowerbed[i+1]==0) {count++;flowerbed[i]=1;} 
            if(count==n) return true;
        }
        if(flowerbed[len-2]==0&&flowerbed[len-1]==0) {count++;if(count==n) return true;}
        return false;
    }
};

```
# 分析
此题很简单，只需要判断是否有连续的三个0即可。同时注意一下边界情况。自己在写的时候还是有很多细节没有注意到，修修补补才过。
