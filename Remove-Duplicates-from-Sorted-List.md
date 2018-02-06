# Remove Duplicates from Sorted List
链表的使用
## Description
 Given a sorted linked list, delete all duplicates such that each element appear only once.

For example, 

Given 1->1->2, return 1->2. 

Given 1->1->2->3->3, return 1->2->3.  
## 解题过程
说实话，这道题，我一看到是链表就打怵，因为之前就没学好链表，哎呀妈呀

基本的思路应该是：删除有序链表中的相同的节点值，遍历链表，设置一个临时变量用于存储当前节点的指针，比较当前节点的值与下一个节点值是否相同，  若相同则删除下一个节点，并让指针指向下下一个节点，若下一个节点的指针为空则退出，若两个节点值不相等则指针向后移动一位，继续比较

直接上代码，妈耶，这相当于重新学一遍了--零基础写链表
```
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
struct ListNode* deleteDuplicates(struct ListNode* head) {
    struct ListNode *temp, *temp1, *p;
    p = head;
    if(head == NULL){ //若链表为空，直接返回
        return NULL;
    }
    temp1 = temp = NULL;  //将中间值赋值为null
    while(p->next != NULL){
        temp = p->next;
        if(p->val == temp->val){
            if(temp->next != NULL){
                temp1 = p->next->next;
                p->next->next = NULL;
                p->next = temp1;
            }else{
                p->next = NULL;
                break;
            }
        }else{
            p = temp;
        }
    }
    return head;
}
```
### 链表
先看一下blog回顾下好了[link](https://www.cnblogs.com/tao560532/articles/2199280.html)
