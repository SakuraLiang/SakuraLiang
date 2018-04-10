# 题目
给定两个非空链表来代表两个非负整数，位数按照逆序方式存储，它们的每个节点只存储单个数字。将这两数相加会返回一个新的链表。

你可以假设除了数字 0 之外，这两个数字都不会以零开头。
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
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        int up=0;
        ListNode node = ListNode(0);
        ListNode* head = &node;
        while(l1||l2||up)
        {
            int temp = (l1?l1->val:0)+(l2?l2->val:0)+up;
            head->next = new ListNode(temp%10);
            up = temp/10;
            head = head->next;
            l1 = l1?l1->next:l1;
            l2 = l2?l2->next:l2;
        }
        return node.next;
    }   
};

```
# 分析
巧妙地利用了三元运算符？，是我没有想到的地方。自己在写的时候，按照样例输入，输出的最后一位少了一位，没有把最后一位如果有之前的进位这一情况包括进去。这种解法很好的解决了这一问题。
