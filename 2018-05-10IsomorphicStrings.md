# 题目
给定两个字符串 s 和 t，判断它们是否是同构的。

如果 s 中的字符可以被替换得到 t ，那么这两个字符串是同构的。

所有出现的字符都必须用另一个字符替换，同时保留字符的顺序。两个字符不能映射到同一个字符上，但字符可以映射自己本身。
# 解法
```ruby
class Solution {  
public:  
     string transferStr(string s){  
        char table[128] = {0};  
        char tmp = '0';  
        for (int i=0; i<s.length(); i++) {  
            char c = s.at(i);  
            if (table[c] == 0) {  
                table[c] = tmp++;  
            }  
            s[i] = table[c];  
        }  
        return s;  
    }  
    bool isIsomorphic(string s, string t) {  
          
        if (s.length() != t.length()) {  
            return false;  
        }  
        if (transferStr(s) == transferStr(t)) {  
            return true;  
        }  
        return false;  
    }  
}; 
```
# 分析
构造一个函数来进行字符串转换，用数字依次来表示字母。直接将两串字符串都转换，看转换结果是否一样。
