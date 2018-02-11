# Merge Two Sorted Lists
链表的使用
## Problem
Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.
## 代码实现
```ruby
struct ListNode* mergeTwoLists(struct ListNode* l1, struct ListNode* l2) {
    struct ListNode * list1=l1,* list2=l2,*p=NULL,*pre=NULL,*m=NULL;
        if(l1&&!l2)
            return l1;
        if(!l1&&l2)
            return l2;
        if(!l1&&!l2)
            return NULL;
        while(list1&&list2)
        {
            if(p)
                pre=p;  //当没有
            if(list1->val<=list2->val)
            {
                p=list1;  
                list1=list1->next;  //不要忘记将链表元素替换
            }
            else 
            {
                p=list2;
                list2=list2->next;
            }
            if(!m)
                m=p;
            if(pre)
               pre->next=p; 
        }
    if(list1)
    {
        p->next=list1;
    }
    if(list2)
    {
        p->next=list2;
    }
    return m;
}
```
## 总结
链表的使用
