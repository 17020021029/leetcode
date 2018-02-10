# Maxmum Depth of Binery Tree
求二叉树的深度
## Problem:
Given a binary tree, find its maximum depth.</br>
The maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.
## 分析
二叉树本来就是递归定义的，因此对它的操作也基本都是递归，此题也是
## 实现
### 一
```ruby
int maxDepth(struct TreeNode* root) {
    int depth=0;  
    if(root!=NULL)
    {
        int leftdepth=maxDepth(root->left);
        int rightdepth=maxDepth(root->right);
        depth=leftdepth>=rightdepth?leftdepth+1:rightdepth+1;
    }
    return depth;    
}
```
### 二
新建一个函数，更好理解
```ruby
int maxDepth(struct TreeNode* root) {
    return findDepth(root,0);
}
int findDepth(struct TreeNode* root,int depth)
{
    if(!root)
        return depth;
    int rightdepth=findDepth(root->right,depth+1);
    int leftdepth=findDepth(root->left,depth+1);
    if(rightdepth>leftdepth)    return rightdepth;
    return leftdepth;
}
```
# Minimum Depth of Binery Tree
## Problem 
Given a binary tree, find its minimum depth.</br>
The minimum depth is the number of nodes along the shortest path from the root node down to the nearest leaf node.
## 分析
与求最大深度的区别，最大深度只需要遍历二叉树，那返回值就等于找到的最大值；而最小深度需要考虑根其中一个子树是否为0，若为0，则深度为不为0的值
## 实现一
不能排查没有左右子树其中之一的情况,[1,2]时就已经出错
```
int minDepth(struct TreeNode* root) {
    int depth;
    if(root!=NULL)
    {
        int leftdepth=minDepth(root->left);
        int rightdepth=minDepth(root->right);
        if(leftdepth==0||rightdepth==0)
            depth=leftdepth+rightdepth+1;
        depth=leftdepth>=rightdepth?rightdepth+1:leftdepth+1;
    }
    return depth;
}
```
## 二(AC)
```ruby
int minDepth(struct TreeNode* root) {
    if(root==NULL)  return 0;
    int left=minDepth(root->left)+1;
    int right=minDepth(root->right)+1;
    if(root->left==NULL)
        return right;
    else if(root->right==NULL)
        return left;
    else return left>=right?right:left;
}
```
