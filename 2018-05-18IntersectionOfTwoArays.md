# 题目
给定两个数组，写一个函数来计算它们的交集。
# 解法
```ruby
class Solution {
public:
    vector<int> intersection(vector<int> &nums1, vector<int> &nums2) {
        vector<int> array;
        sort(nums1.begin(), nums1.end());
        sort(nums2.begin(), nums2.end());
        int i = 0, j = 0;
        while (i < nums1.size() && j < nums2.size()) {
            if (nums1[i] < nums2[j]) ++i;
            else if (nums1[i] > nums2[j]) ++j;
            else {
                array.push_back(nums1[i]);
                ++i;
                ++j;
                while (nums1[i] == nums1[i - 1]) ++i;
                while (nums2[j] == nums2[j - 1]) ++j;
            }
        }
        return array;
    }
};
```
# 分析
先排序，再进行处理。
# 题目

给定两个数组，写一个方法来计算它们的交集。

例如:
给定 nums1 = [1, 2, 2, 1], nums2 = [2, 2], 返回 [2, 2].

注意：

   输出结果中每个元素出现的次数，应与元素在两个数组中出现的次数一致。
   我们可以不考虑输出结果的顺序。
# 解法
```ruby
class Solution {
public:
    vector<int> intersect(vector<int>& nums1, vector<int>& nums2) {
      vector<int>array;
      sort(nums1.begin(),nums1.end());
      sort(nums2.begin(),nums2.end());
      int i=0,j=0;
      while(i!=nums1.size()&&j!=nums2.size())
      {
          if(nums1[i]==nums2[j])
          {
              array.push_back(nums1[i]);
              i++;
              j++;
          }
         else if(nums1[i]<nums2[j])
          {
              i++;
          }
          else if(nums1[i]>nums2[j])
          {
              j++;
          }
          else 
          {
              i++;
              j++;
          }
      }
        return array;
    }
};
```
 # 分析
 还是先排序再处理，因为允许重复，去掉比较的部分。
