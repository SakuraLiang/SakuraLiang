# 题目
Given a non-empty integer array of size n, find the minimum number of moves required to make all array elements equal, where a move is incrementing n - 1 elements by 1.
# 解法

```ruby
class Solution {
public:
    int minMoves(vector<int>& nums) {sort(nums.begin(),nums.end());
        if(nums.size()==1) return 0;
        if(nums.size()==2) return nums[1]-nums[0];
        int count=0;
        while(nums[0]!=nums[nums.size()-1]){
            for(int i=0;i<nums.size()-2;i++){
                nums[i]++;count++;
            }
            sort(nums.begin(),nums.end());
        }
        return count;
    }
};

```
# 分析
我的思路是，把数组进行排序，然后把n-1个数都加1，加一次计数器的值加1加完之后再排序判断最后一个数跟第一个数是否相等，如果相等，则返回计数器的值.但出现的问题仍然是数据一大算法便超时。
# 网上的答案

```ruby
class Solution {
  public:
      int minMoves(vector<int>& nums) {
          sort(nums.begin(), nums.end());
          int len = nums.size(), res = 0;
          
          for (int i = 1; i < len; i++) {
              res += nums[i] - nums[0];
          }
         
         return res;
     }
 };

```
# 分析
每次把最小的n-1个数加1相当于把最大的数减一，最后所有的数都要减到跟最小值一样大，因此，只需要计算数组中的数跟最小值的差的累和即可。
