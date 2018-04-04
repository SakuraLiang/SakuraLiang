# 题目
给定一个有序的链表，删除所有有重复数字的节点，只保留原始列表中唯一的数字。

例如：
给定 1->2->3->3->4->4->5 ，则返回 1->2->5
给定 1->1->1->2->3 ，则返回 2->3
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
    ListNode* deleteDuplicates(ListNode* head) {
        if(head==NULL || head->next==NULL)
            return head;

        ListNode *pDel=new ListNode(0);
        pDel->next=head;
        
        ListNode *prev=pDel;
        ListNode *curr=prev->next;
        
        while(curr->next){
            if(curr->next->val!=curr->val){
                if(prev->next==curr)
                    prev=curr;
                else
                    prev->next=curr->next;
            }
            curr=curr->next;
        }
        
        if(prev->next!=curr)
            prev->next=curr->next;
        
        return pDel->next;
    }
};

```
# 分析
这道题的做法是，新建一个指针用来指向头指针，再建立两个指针，一个指针用来遍历链表，当遍历的指针指向的数和下一个数相等时，直接向右移。当两个元素不等时，判断另一个指针（一开始时指向的是头指针）指向的数是否与遍历指针指向的数相等，如果相等，指向头指针的指针指向遍历指针所指向的数，这样新建立链表的第一个元素就是未重复的第一个数。然后跟着遍历下去，将未重复元素连接起来，形成新的链表。
