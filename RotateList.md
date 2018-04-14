# 题目
给定一个链表，将链表向右旋转 k 个位置，其中 k 是非负数。
# 尝试

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
    ListNode* rotateRight(ListNode* head, int k) {
        int len=0;
        ListNode*p=head;
        while(p)
        {
            len++;
            p=p->next;
        }
        if(len>=k) k=k%len;
        if(len==0||k==0) return p; 
        ListNode*temp=head;
        int n=len-k;
        while(n)
        {
            temp=temp->next;
            (n)--;
        } 
        p=temp;
        while(head)
        {  
            p=p->next;
            p=head;
            head=head->next;
        }
        p=temp;
        return p;
    }
};

```
# 分析
返回的只有最后k个元素。前后两部分没有连接起来。
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
    ListNode* rotateRight(ListNode* head, int k) {
          if(head==NULL){  
            return head;  
        }  
        ListNode* temp=head;  
        int len=1;  
        while(temp->next!=NULL){  
            temp=temp->next;  
            len++;  
        }     
        temp->next=head;  
        k=k%len;  
        for(int i=0;i<len-k-1;i++){  
            head=head->next;  
        }  
        temp=head;  
        head=head->next;  
        temp->next=NULL;  
        return head;
    }
};

```
