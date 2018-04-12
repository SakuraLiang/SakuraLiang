# 题目
给定一个链表，对每两个相邻的结点作交换并返回头节点。
# 解法

```ruby
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* swapPairs(ListNode* head) {
        if(head == NULL || head->next == NULL)  
            return head;    
        ListNode* p = head;   
        ListNode* q = head->next;  
        ListNode* r = NULL;  
        head = q;  
        while(p != NULL && q != NULL)  
        { 
            p->next = q->next;  
            q->next = p;  
            if(r != NULL)  
            r->next = q;    
            r = p;  
            p = p->next;  
            if(p != NULL)  
            q = p->next;  
        }  
        return head; 
        
    }
};
```
# 分析
利用两个指针来不断交换相邻节点的next，一个指针来保存上一节点。自己绕来绕去饶了好久...
