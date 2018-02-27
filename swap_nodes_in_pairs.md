# Swap Nodes in Pairs
## Problem
Given a linked list, swap every two adjacent nodes and return its head.

For example,
Given 1->2->3->4, you should return the list as 2->1->4->3.

Your algorithm should use only constant space. You may not modify the values in the list, only nodes itself can be changed.
## 问题分析
交换每两个相邻的节点的数据，题目没提到考虑奇数个节点的情况，所以只需考虑偶数个即可</br>
## 代码实现
```ruby
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
struct ListNode* swapPairs(struct ListNode* head) {
    int temp;
    struct ListNode* cur=head;
    while(head!=NULL && head->next!=NULL)
    {
        temp=head->val;
        head->val=head->next->val;
        head->next->val=temp;
        head=head->next->next;
    }
    return cur;
}
```
## 总结
问题很简单，终于意识到了用链表处理问题的优越性，如果用数组处理起来，需要设置很多变量，处理起来就相对麻烦，其实也不难
自己测试的代码，貌似还可以实现
```
#include<stdio.h>
int main()
{
  int n;
  printf("请输入一个大于0的偶数\n");
  scanf("%d",&n);
  int a[n];
  for(int i=0;i<n;i++)
    scanf("%d",&a[i]);
  for(int i=0;i<n;i++)
  {
  int temp;
  temp=a[i];
  a[i]=a[i+1];
  a[i+1]=temp;
  i++;
  }
  for(int i=0;i<n;i++)
  printf("%d",a[i]);
  return 0;
  }
  ```
