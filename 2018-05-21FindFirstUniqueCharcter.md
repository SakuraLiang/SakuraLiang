# 题目

给定一个字符串，找到它的第一个不重复的字符，并返回它的索引。如果不存在，则返回 -1。
# 解法
```ruby
class Solution {
public:
    int firstUniqChar(string s)
    {
        vector<int>count(26);
        for (int i=0;i<(int)s.size();i++)
        {
            count[s[i]-'a']++;
        }
        for (int i=0;i<(int)s.size();i++)
        {
            if (count[s[i]-'a']==1)
                return i;
        }
        return -1;
    }
};
```
# 分析
先利用动态数组保存每个单词出现的频率，再遍历一遍得出只出现一次的
