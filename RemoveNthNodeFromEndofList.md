# 题目
给定一个链表，删除链表的倒数第 n 个节点并返回头结点。
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
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        ListNode*p=head;
        if(n==0)
            {
                return p;
            }
        int len=0;
        
        while(p!=NULL)
        {
         len++; 
         p=p->next;
        }
        if(len==1)
        {
         return NULL;
        }
        len=len-n+1;
        p=head;
        if(len==1)
        {
            p=p->next;
            return p;
        }
        while(p!=NULL)
        {
            len--;
            if(len==1) 
            {
                p->next=p->next->next;
                break;
            } 
            p=p->next;
        }
        p=head;
        return p;
    }
};
```
# 分析
虽然题目问我能不能遍历一次实现，不过我想了想还是用了两次把这道题做出来了。先做出来，再仔细想想有没有更好的办法咯。我的思路是，先遍历一次，求出节点总数，再根据给的数据n得出，要删去的是正数的第几个，再用一次遍历删去即可。写的时候有碰到很多小问题导致不能通过，但是，根据不能通过的样例，再修修补补就可以通过了。
# 解法2

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
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        ListNode*p=head; 
        if(n==0)
        {
         return p;   
        }
        
        ListNode*q=head;
        for(int i=0;i<n-1;i++)
        {
            q=q->next;
        }
        if(q->next==NULL)
        {
            p=p->next;
            return p;
        }
        while(q->next->next!=NULL)
        {
            p=p->next;
            q=q->next;
        }
        p->next=p->next->next;
        p=head;
        return p;
  }
};
```
# 分析
果然自己再想想是能解决的。利用了之前做过的双指针，先让两个指针都指向头结点，然后，让其中一个指针先走n-1步，两个指针再同时走，当先走的指针的下下个为NULL时，后走的指针的下一个就是要删除的节点，删掉就okay啦。最开始写出来没有考虑到，删除的节点是第一个这种情况，看到没通过的样例改改就okay了。虽然这样做真的挺方便，不过，一直这样思考问题不全面也不是办法啊。
