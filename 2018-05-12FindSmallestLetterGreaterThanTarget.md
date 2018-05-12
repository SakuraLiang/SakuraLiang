# 题目
给定一个只包含小写字母的有序数组letters 和一个目标字母 target，寻找有序数组里面比目标字母大的最小字母。

数组里字母的顺序是循环的。举个例子，如果目标字母target = 'z' 并且有序数组为 letters = ['a', 'b']，则答案返回 'a'。
# 解法
```ruby
class Solution {
public:
    char nextGreatestLetter(vector<char>& letters, char target) {
        if (letters.back() <= target) return letters.front();
        int low = 0, high = letters.size() - 1;
        while (low < high) {
            int mid = (low + high) / 2;
            if (target < letters[mid]) high = mid;
            else low = mid + 1;
        }
        return letters[low];
    } 
};
```
# 分析
抽象为在给定的有序数组中寻找最接近目标元素的数。用二分查找。
