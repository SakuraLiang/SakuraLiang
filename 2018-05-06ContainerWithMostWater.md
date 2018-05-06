# 题目
给定 n 个非负整数 a1，a2，...，an，每个数代表坐标中的一个点 (i, ai) 。画 n 条垂直线，使得垂直线 i 的两个端点分别为 (i, ai) 和 (i, 0)。找出其中的两条线，使得它们与 x 轴共同构成的容器可以容纳最多的水。

注意：你不能倾斜容器，n 至少是2。
# 解法1
```ruby
class Solution {
public:
    int maxArea(vector<int>& height) {
        int len=height.size();
        int *pslow=&height[0];        
        int area=0;      
        while(pslow!=&height[len-1])
        {
            int *pfast=&height[0];
            while(pfast!=&height[len])
            {
                area=max(area,min(*pfast,*pslow)*(int)(pfast-pslow));
                pfast++;
            }
            pslow++;
        }
     return area; 
    }
};
```
# 分析
自己写的双重循环版，数据一大就会超时...真是毫无悬念...
# 解法2
```ruby
class Solution {
public:
    int maxArea(vector<int>& height) {
        int len=height.size();
        int *pslow=&height[0];
        int *pfast=&height[len-1];
        int area=0;      
        while(pfast!=pslow)
        {
          area=max(min(*pfast,*pslow)*(int)(pfast-pslow),area);
            if(*pslow<=*pfast) pslow++;
            else pfast--;
        }
     return area; 
    }
};
```
# 分析
看了网上的分析，写出了这个版本。思路是：先从数组的起点和终点开始，然后从较短边开始移动，因为如果移动较大边，面积肯定会减小，用了快慢两个指针...（虽然这种情况并不是快慢指针...名字而已...），慢指针是从起点开始的指针，向终点移动，快指针是从终点开始的指针，向起点移动，每一次移动都保留当前面积的最大值，直到两个指针相遇。
