# Romove Nth Node From End of List
链表
## Problem
Given a linked list, remove the nth node from the end of list and return its head.

For example,

   Given linked list: 1->2->3->4->5, and n = 2.

   After removing the second node from the end, the linked list becomes 1->2->3->5.

Note:
Given n will always be valid.
Try to do this in one pass.
## 问题分析
题目很简单，就是去除链表中某个特殊的链节
## 解题思路
定义两个头指针，一个用来计算链表长度,一个用来删除链节
## 代码实现
```ruby
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
struct ListNode* removeNthFromEnd(struct ListNode* head, int n) {
    struct ListNode* p=head;
    struct ListNode* q=head;
    int listlen=0;
    int count=0;
    if(head==NULL)
        return head;
    while(p)
    {
        listlen++;
        p=p->next;
    }
    count=listlen-n;
    int i=0;
    while(q&&i<count-1)
    {
        q=q->next;
        i++;
    }
    if(count==0)
    {
        head=head->next;
    }
    else{
        q->next=q->next->next;
    }
    return head;
}
```
