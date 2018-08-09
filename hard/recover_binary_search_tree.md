## Problem 
 wo elements of a binary search tree (BST) are swapped by mistake.

Recover the tree without changing its structure.
Note:
A solution using O(n) space is pretty straight forward. Could you devise a constant space solution?
## 代码实现
递归算法
```C++
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
    vector<int> postorderTraversal(TreeNode* root) {
        vector<int> res;
        dfs(root,res);
        return res;
    }
    void dfs(TreeNode* root,vector<int>& res){
        if(!root)   return;
        if(root->left) dfs(root->left,res);
        if(root->right) dfs(root->right,res);
        res.push_back(root->val);
    }
};
```
迭代算法（栈的应用）
```C++
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
    vector<int> postorderTraversal(TreeNode* root) {
        stack<TreeNode*> t;
        t.push(root);
        vector<int> res;
        if(!root) return res;
        while(!t.empty()){
            TreeNode* temp=t.top();
            if(temp->left){
                t.push(temp->left);
                temp->left=NULL;
            }
            else if(temp->right){
                t.push(temp->right);
                temp->right=NULL;
            }
            else{
                res.push_back(temp->val);
                t.pop();
            }
        }
        return res;
    }
};
```
