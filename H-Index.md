# 题目
给定一位研究者的论文被引用次数的数组（被引用次数是非负整数）。写一个方法计算出研究者的H指数。

H-index定义: “一位科学家有指数 h 是指他（她）的 N 篇论文中至多有 h 篇论文，分别被引用了至少 h 次，其余的 N - h 篇论文每篇被引用次数不多于 h 次。"

例如，给定 citations = [3, 0, 6, 1, 5]，意味着研究者总共有 5 篇论文，每篇论文相应的被引用了 3, 0, 6, 1, 5 次。由于研究者有 3 篇论文每篇至少被引用了 3 次，其余两篇论文每篇被引用不多于 3 次，所以他的 h 指数是 3。
# 解法
```ruby
class Solution {
public:
    int hIndex(vector<int>& citations) {
        if (citations.empty())
            return 0;
        sort(citations.begin(),citations.end());
        int len=citations.size(),H=0;
        for (int i=len-1;i>=0;--i)
        {
            int h=len-i;
            if (citations[i]>=h&&h>H)
            {
                H=h;
            }
            else{
                break;
            }
        }
        return H;
    }
};
```
# 分析
最简单的做法就是，先排序，然后开始遍历，如果遍历到的位置对应的数小于位数加一，说明之后的不会再大于，即是H指数、