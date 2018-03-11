# 题目
给定一个排序数组和一个目标值，如果在数组中找到目标值则返回索引。如果没有，返回到它将会被按顺序插入的位置。
# 解法

```ruby
int searchInsert(int* nums, int numsSize, int target) {
    int i;
    for( i=0;i<numsSize;i++){
        
        if(nums[i]>=target) 
            break;}
  return i;
}

```
# 分析
此题比较简单，只需按序查找并进行一个判断即可。由此题联想，如果是需要输出按序插入后的数组，可以用链表解决。
