### 二叉树的镜像

---

#### 1. 题意

&emsp;&emsp;请完成一个函数，输入一个二叉树，该函数输出它的镜像

#### 2. 思路

**递归**

#### 3. Code

```
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
    TreeNode* reverseTree(TreeNode* root){
        if(!root)return NULL;
        TreeNode* left = root->left;
        TreeNode* right = root->right;
        root->left = reverseTree(right);
        root->right = reverseTree(left);
        return root;
    }
    TreeNode* mirrorTree(TreeNode* root) {
        return reverseTree(root);
    }
};
```