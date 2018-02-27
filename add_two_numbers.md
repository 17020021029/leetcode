# Add Two Numbers
链表
## problem
You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

Example

Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8
Explanation: 342 + 465 = 807.
## 问题分析
目的很简单——将链表当做整数相加，且链表的顺序为位数从小到大的顺序
## 解题思路
1. 定义头指针，指向当前的一个位置，并分配内存；
2. 定义整型carry标记进位
3. 遍历，相加两个链表的数据和进位值
4. 若遍历完，还有进位，则再申请节点赋值
5 。最后一个节点指向空，返回头指针的指针域
## 代码实现
```ruby
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
struct ListNode* addTwoNumbers(struct ListNode* l1, struct ListNode* l2) {
    struct ListNode* header=(struct ListNode*)malloc(sizeof(struct ListNode));  //定义头指针并分配内存
    struct ListNode* cur=header;             //头指针指向当前位置
    int carry=0;                         //carry代表进位
    while(l1!=NULL||l2!=NULL)
    {
        int sum=0,a,b;
        a=(l1!=NULL)?l1->val:0;
        b=(l2!=NULL)?l2->val:0;
        sum=a+b+carry;
        carry=sum/10;
        cur->next=(struct ListNode*)malloc(sizeof(struct ListNode));
        cur=cur->next;
        cur->val=sum%10;
        if(l1!=NULL)
            l1=l1->next;
        if(l2!=NULL)
            l2=l2->next;
    }
    if(carry>0)                        //链表结束后是否还有进位
    {
        cur->next=(struct ListNode*)malloc(sizeof(struct ListNode));
        cur=cur->next;
        cur->val=carry;
    }
    cur->next=NULL;                   //最后一个节点指向空
    return header->next;
}
```
## 总结
链表的创建和使用
