# 题目
删除链表中等于给定值 val 的所有元素。
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
    ListNode* removeElements(ListNode* head, int val) {
        ListNode * p=new ListNode(0);  
       p->next=head;  
       ListNode * cur=head;  
       ListNode * pre=p;  
       while(cur)  
       {  
           if(cur->val!=val)  
           {  
               pre=cur;  
               cur=cur->next;  
           }  
           else  
           {  
               pre->next=cur->next;  
               cur=pre->next;  
           }  
       }  
       return p->next;  
    }
};

```
# 分析
先创建一个指针，指向头结点。(此种方法的应用在其他很多题也有用到)再建立两个指针用来遍历，进行删除操作。
# 题目
请编写一个函数，使其可以删除某个链表中给定的（非末尾的）节点，您将只被给予要求被删除的节点。

比如：假设该链表为 1 -> 2 -> 3 -> 4  ，给定您的为该链表中值为 3 的第三个节点，那么在调用了您的函数之后，该链表则应变成 1 -> 2 -> 4 
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
    void deleteNode(ListNode* node) {
        if (!node || !node->next)  
        return;  
    node->val=node->next->val;  
    node->next=node->next->next;  
    }
};

```
# 分析
一开始没有读懂题意，后来一查才知道题目要求是，给定链表的某一节点，然后删除。由于没有给出整个链表，所以解决方案是，将当前节点的下一个节点赋值给当前节点，再跳过下一节点。
