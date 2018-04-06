# 题目
给定一个链表，判断链表中否有环。

补充：
你是否可以不用额外空间解决此题？
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
    bool hasCycle(ListNode *head) {
        ListNode*f=head;
        ListNode*s=head;
        while(f!=NULL&&s!=NULL&&s->next!=NULL)
        {f=f->next;
         s=s->next->next;
        if(f==s) return true;}
         return false;}
        
};

```
# 分析
在有环的链表之中，如果用一个指针来遍历下去就会无限循环的。抓住这一点，利用两个指针，一个每次移动俩步，一个每次移动一个，如果有环就一定会相遇。补充循条件为，两个指针都不是NULL，且每次移动一步的指针的next不为NULL。一旦两个指针相遇，就返回true。如果没有，就返回false。
