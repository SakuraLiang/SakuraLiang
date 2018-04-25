# 题目
给定一个单链表 L：L0→L1→…→Ln-1→Ln ，
将其重新排列后变为： L0→Ln→L1→Ln-1→L2→Ln-2→…

你不能只是单纯的改变节点内部的值，而是需要实际的进行节点交换
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
    void reorderList(ListNode *head) {
        if(head==NULL)
			return;
		int len=getlistlen(head);
		ListNode *head1=NULL , *head2=NULL ;
		dividelist( head, len , head1 , head2 );
		head2 = reverseList(head2);
        mergeList(head1, head2);
    }
private:
	int getlistlen(ListNode *head)
	{
		int len=0;
		while(head)
		{
			len++;
			head = head->next;
		}
		return len;
	}

	void dividelist(ListNode *head , int len , ListNode *&head1 , ListNode *&head2)
	{
		int half = (len+1)/2;
		ListNode *first=head;
		head1 = head;
		for(int i=0; i<half-1; i++)
		{
			first = first->next;
		}
		head2 = first->next;
		first->next = NULL;
	}

	ListNode* reverseList(ListNode* head)
    {
		if( head == NULL)
			return NULL;
		ListNode *p = head->next;
		head->next = NULL;
		while(p)
		{
			ListNode *temp = p;
			p = p->next;
			temp->next = head;
			head = temp;
		}
		return head;
    }
    void mergeList(ListNode* head1, ListNode* head2)
    {
        while(head2)
		{
			ListNode *temp = head2;
			head2 = head2->next;

			temp->next = head1->next;
			head1->next = temp;
			head1 = head1->next->next;
		}
    }
};
```
# 分析
先把链表划分为两个部分，然后将后半部分倒序，最后将后半部分链表依次插入前半部分。我没有想到的点是，将后半部分倒序后插入。
