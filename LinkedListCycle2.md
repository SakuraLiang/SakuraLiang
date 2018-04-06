# 题目
给一个链表，返回链表开始入环的第一个节点。 如果链表无环，则返回 null。

说明：不应修改给定的链表。

补充：
你是否可以不用额外空间解决此题？
# 解法

```ruby
class Solution {
public:
    ListNode *detectCycle(ListNode *head) {
        ListNode*f=head;
        ListNode*s=head;
        while(f!=NULL&&s!=NULL&&s->next!=NULL)
        {f=f->next;
         s=s->next->next;
        if(f==s){
            f=head;  
        while(f!=s){  
            s=s->next;  
            f=f->next;  
        }  
        return s; 
        }
        }
         return NULL;
        }
};

```
# 分析
在判断是否有环的基础上，只需要在没有环时返回NULL，有环时返回环的起始点。在判断是否有环的过程中，快指针是慢指针移动速度的两倍，在相遇点，快指针比慢指针多走的即是head到入环点加上慢指针在环中走过的部分。环的长度就为head到入环点的距离加上慢指针入环后走过的距离。快指针走过的减去慢指针入环后走过的，即是head到入环点的距离。此时，把快指针指向head，再让两个指针以同样的速度移动，两个指针必定会在入环点相遇。
我在写的时候，没有想到可以通过类似于数学的方法来解决这道题。
此外，还看到了快慢指针的拓展应用，用来判断两个无环链表是否相交，只需要把其中一个链表头节点和尾结点相连，然后判断剩下的链表是否有环即可。
