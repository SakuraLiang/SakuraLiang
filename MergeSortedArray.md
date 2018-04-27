# 题目
给定两个有序整数数组 nums1 和 nums2，将 nums2 合并到 nums1 中，使得 num1 成为一个有序数组。

说明:

初始化 nums1 和 nums2 的元素数量分别为 m 和 n。
你可以假设 nums1 有足够的空间（空间大小大于或等于 m + n）来保存 nums2 中的元素。
# 解法
```ruby
class Solution {
public:
    void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
        if (n == 0)  
        return;  
    if (m == 0 && n != 0) {  
        for (int i = 0; i < n; i++) {  
            nums1[i] = nums2[i];  
        }  
    }  
    int i = m - 1;  
    int j = n - 1;   
    int k = m + n - 1; 
  
    while (i >= 0 && j >= 0) {  
        if (nums1[i] > nums2[j]) { 
            nums1[k] = nums1[i];      
            i--;            
        } else {  
            nums1[k] = nums2[j];  
            j--;  
        }  
        k--;  
    }  
    while (i >= 0) { 
        nums1[k] = nums1[i];  
        i--;  
        k--;  
    }  
    while (j >= 0) {  
        nums1[k] = nums2[j];  
        j--;  
        k--;  
    }   
    }
};
```
# 分析
因为给的数组已经有顺序，所以在处理这道题的时候，只需依次从后面的元素开始比较，并从末尾开始放入元素。
