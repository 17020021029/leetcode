# [Same Tree](https://leetcode.com/problems/same-tree/description/)
二叉树基础题
## Problem
 Given two binary trees, write a function to check if they are the same or not.</br>
Two binary trees are considered the same if they are structurally identical and the nodes have the same value. 
## 分析&思路
数据结构最基础的题，判断两个二叉树相等:结构相同以及节点的值一一对应。</br>
两个二叉树同步遍历，过程中只要结构有不同或节点的值不同，则肯定不相等，否则，能一直遍历，则两二叉树相等
## 代码实现
```ruby
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    bool isSameTree(TreeNode* p, TreeNode* q) {
        if(p==NULL&&q==NULL)
            return true;
        if(NULL==p||NULL==q||p->val!=q->val||!isSameTree(p->right,q->right)||!isSameTree(p->left,q->left))
            return false;
        return true;
    }
};
```
## 总结
理解了[二叉树](https://baike.baidu.com/item/%E4%BA%8C%E5%8F%89%E6%A0%91/1602879?fr=aladdin#3)的结构，再写这道题不难，就是二叉树遍历,关键是再掌握二叉树的知识。
