# 148 Sort List
https://leetcode.com/problems/sort-list/
## 知识点
归并排序
参考代码https://blog.csdn.net/geekmanong/article/details/50451339

书中介绍P61 P83
## 代码
merge排序没写
```c++
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
    ListNode* sortList(ListNode* head) {
        if(head==NULL||head->next==NULL)
             return head;//无法继续往下分
        //找到中间节点
        ListNode* fast=head,slow=head;
        while(fast->next!=NULL&&slow->next->next!=NULL){
            fast=fast->next->next;
            slow=slow->next;
        }
        //将list分为两部分
        fast=slow;
        slow=fast->next;
        fast->next=NULL;
        
        ListNode *l1=soryList(head);//前半段排序
        ListNode *l2=sortList(slow);//后半段排序
        return merge(l1,l2);//归并两列表
    }
    ListNode* merge(ListNode* l1,ListNode *l2){
        
    }
};
```
