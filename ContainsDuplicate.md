# 题目
给定一个整数数组，判断是否存在重复元素。

如果任何值在数组中出现至少两次，函数应该返回 true。如果每个元素都不相同，则返回 false。
# 解法1

```ruby
class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {
       
        sort(nums.begin(),nums.end());
        int i=0;
        int count=0; 
        if(nums.size()<=1) count=0;
       if(nums.size()>1) { while(i<nums.size()-1){
            if(nums[i]==nums[i+1]) count++;
            if(count>0) break;i++;}}
        return count;
    }
};

```
# 分析
这一种解法只是进行先排序，然后遍历一遍，判断前后两个数是否相等。如果有相等的，则计数的变量加一，最后返回计数的变量。当然，要排除数组为空和只有一个元素这两种可能。
# 解法2
```ruby
class Solution {
public:
    bool containsDuplicate(vector<int>& nums) {           
        if(nums.size()<=1) {return false;}
        if(nums.size()>1){
       map<int,int>numbers;
        for(int i=0;i<nums.size();i++){
            if(numbers.find(nums[i])==numbers.end()) numbers[nums[i]]++;
            else return true;
        }} return false;}
};

```

# 分析
利用map函数。如果某元素出现过，则返回true。如果没有，则计数器加一。可以用find函数也可用count。二者都能通过，只是find要注意numbers.end()。
