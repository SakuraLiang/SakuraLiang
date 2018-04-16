# 题目

给定一个链表和一个特定值 x，对链表进行分隔，使得所有小于 x 的节点都在大于或等于 x 的节点之前。

你应当保留两个分区中每个节点的初始相对位置。
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
    ListNode* partition(ListNode* head, int x) {
if(head==NULL||head->next==NULL) return head;
        ListNode*p=new ListNode(0);
        ListNode*phead=new ListNode(0);
        ListNode*q=new ListNode(0);
        ListNode*qhead=new ListNode(0);
        ListNode*find=head;
        int m=0;int n=0;
        while(find)
        {
            if(find->val<x&&m==0)
            {
                phead->next=find;
                m++;
            }
            if(find->val>=x&&n==0)
            {
                qhead->next=find;
                n++;
            }
            find=find->next;
            
            if(m*n) break;
        }
        find=head;
        if(phead->next==NULL) return qhead->next;
        if(qhead->next==NULL) return phead->next;
       while(find->next)
        {
            if(find->val<x)
            {   
                p->next=find;p=find;
            }
            if(find->val>=x)
            {
                q->next=find;q=find;
            }
            find=find->next;
        }
        if(find->val<x)
            {   
                p->next=find;
                p=p->next;
                q->next=NULL;
            }
         if(find->val>=x)
            {   
                q->next=find;
                q=q->next;
            }
        p->next=qhead->next;
        p=phead->next;
        return p;
    }
};

```
# 分析
我的思路是，用两个指针来分别保存两部分的头结点，再用两个指针分别链接各自那部分的元素，再用一个来遍历。遍历到最后一个元素之后，判断最后一个元素是大于还是小于，以此来决定存放的位置。最后再把两个部分连接起来。
# 出现过的问题
- 没有把最后一个元素单独拿出来判断时，最后一个元素始终会在最后。改进后最后一个元素只判断它是否小于并在小于时将它接到小的那部分的末尾，结果还是错误，加上判断是否大于并在大于时接到大的那部分的最后。问题解决。
- 在输出的结果与预期结果相同的情况下还是被判断为错误。分析后发现只有在给出的链表全小于那个数和全大于那个数时会发生这种情况，于是把头结点保存到用0初始化后的next，返回相应的head->next。问题解决。
