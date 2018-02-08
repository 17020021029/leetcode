# [Symmetric Tree](https://leetcode.com/problems/symmetric-tree/description/)
对称树
## Problem
Given a binary tree, check whether it is a mirror of itself (ie, symmetric around its center).
## 分析&思路
这个与前面[Same tree]的类似,无非是遍历二叉树，区别是这个是遍历一个二叉树，那么可以从第二个节点开始，旌一个二叉树分成两个，那么只要把左右调换，就与SameTree一样
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
    bool isSymmetric(TreeNode* root) {
        if(root==NULL)  return true;
        if(root->left==NULL&&root->right==NULL) return true;
        return Mirror(root->left,root->right);
    }
    bool Mirror(TreeNode *p,TreeNode *q)
    {
        if(p==NULL&&q==NULL)    return true;
        if(p==NULL||q==NULL||p->val!=q->val||!Mirror(p->left,q->right)||!Mirror(p->right,q->left))  return false;
        return true;
    }
};
```
## 总结
思路与Same tree类似，继续理解掌握二叉树即可
