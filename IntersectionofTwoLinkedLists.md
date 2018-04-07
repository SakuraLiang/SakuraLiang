# 题目
编写一个程序，找到两个单链表相交的起始节点。

 

例如，下面的两个链表：

A:          a1 → a2
                   ↘
                     c1 → c2 → c3
                   ↗            
B:     b1 → b2 → b3
在节点 c1 开始相交。
# 解法

```ruby
class Solution {
public:
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        if(headA==NULL || headB==NULL) return NULL;  
          
        ListNode*p = headA;  
        ListNode*q = headB;  
        int pcount = 0;  
        int qcount = 0;  
        while(p->next != NULL || q->next != NULL) {  
            if(p == q) return p;  
            if(p->next != NULL) p = p->next; else ++qcount;  
            if(q->next != NULL) q = q->next; else ++pcount;  
        }  
        if(p != q) return NULL;  
        p = headA;  
        q = headB;  
        while(pcount-- != 0) {  
            p = p->next;  
        }  
          
        while(qcount-- != 0) {  
            q = q->next;  
        }  
          
        while(p != q) {  
            p = p->next;  
            q = q->next;  
        }  
        return p;  
    }  
};

```
# 分析
这是网上的方法，分别计算两个链表的长度，得出长度差，然后让长链表指针先走长度差的步数，再同时走，相遇的地方即为相交点。
# 自己的

```ruby
class Solution {
public:
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        if(headA==NULL || headB==NULL) return NULL;  
          
        ListNode*p=headA;  
        while(p->next!=NULL) p=p->next;
        p->next=headA;
        ListNode*f=headB;
        ListNode*s=headB;
        while(f!=NULL&&s!=NULL&&s->next!=NULL)
        {f=f->next;
         s=s->next->next;
        if(f==s){
            f=headB;  
        while(f!=s){  
            s=s->next;  
            f=f->next;  
        }  
        return s; 
        }
        }
         return NULL;}
        
};

```
# 分析
结合了上两道题，做法是，将其中一个链表尾指针指向起始点，然后找出第二个链表的入环点。理论上是行得通的吧...可是报错了，链表结构被修改..这样做是不被允许的？？
