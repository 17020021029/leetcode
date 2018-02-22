# Balanced Binery Tree
平衡树
## Problem
Given a binary tree, determine if it is height-balanced.
For this problem, a height-balanced binary tree is defined as:

    a binary tree in which the depth of the two subtrees of every node never differ by more than 1.

Example 1:

Given the following tree [3,9,20,null,null,15,7]:
````
     3    
    / \
   9   20
      /  \
     15   7
````
Return true.

Example 2:

Given the following tree [1,2,2,3,3,null,null,4,4]:
````
       1
      / \
     2   2
    / \
   3   3
  / \
 4   4
````
Return false.

## 解题过程
### Approach1
例子二的情况即不能通过
代码实现
```
int findDepth(struct TreeNode *root)
{
    int depth=0;
    if(root!=NULL)
    {
        int leftdepth=findDepth(root->left);
        int rightdepth=findDepth(root->right);
        depth=leftdepth>=rightdepth?leftdepth+1:rightdepth+1;
    }
    return depth;
}
bool isBalanced(struct TreeNode* root) {
    if(!root)
        return true;
    int l=findDepth(root->left);
    int r=findDepth(root->right);
    if(l!=-1||r!=-1||abs(l-r)<=1)
        return true;
    else 
        return false;
}
```
### Approach2
```ruby
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     struct TreeNode *left;
 *     struct TreeNode *right;
 * };
 */
int findDepth(struct TreeNode *root,int n)
{
    if(!root)
        return n;
    int l=findDepth(root->left,n+1);
    int r=findDepth(root->right,n+1);
    if(l==-1||r==-1||abs(l-r)>1)
        return -1;
    else if(l>r)
        return l;
    else return r;
}
bool isBalanced(struct TreeNode* root) {
    if(findDepth(root,0)!=-1)
        return true;
    else 
        return false;
}
```
## 总结
因为本身对二叉树了解的不深，在我自己看来，两种解法暂时不知道关键区别在哪
