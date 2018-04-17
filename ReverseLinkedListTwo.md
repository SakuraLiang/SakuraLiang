# 题目
反转从位置 m 到 n 的链表。用一次遍历在原地完成反转。
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
    ListNode* reverseBetween(ListNode* head, int m, int n) {
   if(head==NULL||m>n) {
            return NULL;
        }
        ListNode*dummyNode=new ListNode(-1);
        dummyNode->next=head;
        head=dummyNode;
        for(int i=1;i<m;i++) {
            if(head==NULL) {
                return NULL;
            }
            head=head->next;
        }
        ListNode*pre=head;
        ListNode*fNode=head->next;
        ListNode*lastNode=NULL;
        ListNode*curNode=fNode;
        for(int i=m;i<=n;i++) {
            ListNode*tmp=curNode->next;
            curNode->next=lastNode;
            lastNode=curNode;
            curNode=tmp;
        }
        pre->next=lastNode;
        fNode->next=curNode;
        return dummyNode->next;
    }
};
```
# 分析
只需要保存反转开始的节点和结束的节点，反转后连接起来即可。
