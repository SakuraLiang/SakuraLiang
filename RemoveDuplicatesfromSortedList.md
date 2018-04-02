# 题目
Given a sorted linked list, delete all duplicates such that each element appear only once.
For example,
Given 1->1->2, return 1->2.
Given 1->1->2->3->3, return 1->2->3.
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
    ListNode *deleteDuplicates(ListNode *head) {  
        if(head==NULL||head->next==NULL)  
            return head;  
        ListNode* f=head;  
        ListNode* s=head->next;  
        while(s!=NULL){  
            if(s->val==f->val) {  
                s=s->next;  
            }else{  
                f->next=s;  
                f=s;  
                s=s->next;  
            }  
        }  
        f->next=NULL;  
        return head;  
    }  
};  


```
# 分析
此题比较简单，只需判断链表中下一个指向的值是否与上一个相等，如果相等，直接让上一个的next指向下一个的next就可以达到删除目的。另外，在最开始的时候判断链表头指针是否为空，头指针上午next是否为空即可。
