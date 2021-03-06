# 题目
作为一位web开发者， 懂得怎样去规划一个页面的尺寸是很重要的。 现给定一个具体的矩形页面面积，你的任务是设计一个长度为 L 和宽度为 W 且满足以下要求的矩形的页面。要求：

1. 你设计的矩形页面必须等于给定的目标面积。

2. 宽度 W 不应大于长度 L，换言之，要求 L >= W 。

3. 长度 L 和宽度 W 之间的差距应当尽可能小。
你需要按顺序输出你设计的页面的长度 L 和宽度 W。
# 解法
```ruby
class Solution {
public:
    vector<int> constructRectangle(int area) {
     vector<int> result(2, 0);
        int l = sqrt(area), w = sqrt(area);
        while(l * w != area)
        {
            if(l * w < area)
                l++;
            else
                w--;
        }
        result[0] = l;
        result[1] = w;
        return result;   
    }
};
```
# 分析
一开始还想用纯数学的方法来做，可是题目要求全是整数，用数学的方法就会比较麻烦。
