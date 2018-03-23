# 题目
The set S originally contains numbers from 1 to n. But unfortunately, due to the data error, one of the numbers in the set got duplicated to another number in the set, which results in repetition of one number and loss of another number.

Given an array nums representing the data status of this set after the error. Your task is to firstly find the number occurs twice and then find the number that is missing. Return them in the form of an array.

# 解法

```ruby
class Solution {
public:
    int a[10001];
    vector<int> findErrorNums(vector<int>& nums) {
        int n=nums.size();
        for(int i=0;i<n;i++)a[nums[i]]++;
        vector<int> ans;
        for(int i=1;i<=n;i++){
            if(a[i]==2)ans.push_back(i);
        }
        for(int i=1;i<=n;i++){
            if(a[i]==0)ans.push_back(i);
        }
        return ans;
    }
};

```

 #分析
 先将所有的数都在哈希表中判断一遍，然后直接遍历寻找出现两次的数和出现0次的数。还有其他的解法。比如，可以将数组的值从1开始依次减去1到n,出现负数的即为重复的数字。
