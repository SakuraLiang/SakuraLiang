# 题目
合并两个已排序的链表，并将其作为一个新列表返回。新列表应该通过拼接前两个列表的节点来完成。
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
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
                if (l2 == NULL)  
            return l1;  
        if (l1 == NULL)  
            return l2;  
        ListNode *head=new ListNode(0);  
        ListNode *r = head;  
        while (l1 && l2)  
        {  
            if (l1->val == l2->val)  
            {  
                ListNode*p1 = new ListNode(l1->val);  
                ListNode*p2 = new ListNode(l2->val);  
                r->next = p1;  
                r = p1;  
                r->next = p2;  
                r = p2;  
                l1 = l1->next;  
                l2 = l2->next;  
            }  
            else if (l1->val < l2->val)  
            {  
                ListNode*p1 = new ListNode(l1->val);  
                r->next = p1;  
                r = p1;  
                l1 = l1->next;  
            }  
            else  
            {  
                ListNode*p2 = new ListNode(l2->val);  
                r->next = p2;  
                r = p2;  
                l2 = l2->next;  
            }  
        }  
        if (!l1)  
        {  
            r->next = l2;  
        }  
        else  
        {  
            r->next = l1;  
        }  
        ListNode * p = head;  
        head = head->next;  
        delete p;  
        return head;  
    }  
};  

```
# 分析
此题关键在于不仅要合并两个链表，更要把两个本就有序的链表合成后仍为有序状态。首先，如果两个链表其中有一个为空就要返回另一个，这种特殊情况在我自己写的时候并没有考虑到。新建一个头指针和另一个辅助指针，那个指针指向头结点，l1和l2这两个指针指向的都不为空时，判断这两个指针指向的数的大小，如果不一样的大，则让辅助指针指向的数为小的那个，并让那个那个链表对应的指针向右移动。如果一样大，则先后插入两个元素，同时两个链表对应的指针都要向右移动。一旦有个链表遍历完了，则让另一个链表剩下的部分直接加在后面
