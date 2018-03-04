# Partition List
## Problem
Given a linked list and a value x, partition it such that all nodes less than x come before nodes greater than or equal to x.

You should preserve the original relative order of the nodes in each of the two partitions.

For example,
Given 1->4->3->2->5->2 and x = 3,
return 1->2->2->4->3->5. 
## 问题分析
目的很简单，将小于目标值的依次放在前边，其余依次放在后边
## 代码实现
```ruby
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
struct ListNode* partition(struct ListNode* head, int x) {
    struct ListNode *cur=head, *pre=head, *newhead=head, *s_cur=NULL, *s_pre=NULL;    
    while(cur)
    {
        if (cur->val<x)
        {
            if (cur==head)
            {
                head=head->next;
                pre=head;
            }
            else
                pre->next=cur->next;
            if (!s_cur) 
            {
                s_cur=cur;
                newhead=s_cur;
            }
            else
                s_cur->next=cur;
            s_cur=cur;
            if (pre==head)
                cur=head;
            else
                cur=pre->next;
        }
        else
        {
            pre=cur;
            cur=cur->next;
        }
    }
    if (s_cur)
        s_cur->next=head;  
    return newhead;
}
```
