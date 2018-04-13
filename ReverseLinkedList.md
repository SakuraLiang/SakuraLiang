# 题目

反转一个单链表。
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
    ListNode* reverseList(ListNode* head) {
        ListNode *newhead=NULL;
        while(head)
        {
            ListNode *nextNode=head->next;
            head->next=newhead;
            newhead=head;
            head=nextNode;
        }
        return newhead;
    }
};

```
# 分析
不断更新newhead和head。同时，每次都把newhead赋给head->next，再把head赋给newhead，这样就将原来的链表顺序读取，放入newhead之后第一个读取的被一次一次挤到最后。
