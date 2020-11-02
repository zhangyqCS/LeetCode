### 对称的二叉树

---

#### 1. 题意

&emsp;&emsp;请实现一个函数，用来判断一棵二叉树是不是对称的。如果一棵二叉树和它的镜像一样，那么它是对称的

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
    bool check(TreeNode* l, TreeNode* r){
        if(!l && !r)return true;
        if(!l || !r || l->val != r->val)return false;
        return (check(l->left, r->right) && check(l->right, r->left));
    }
    bool isSymmetric(TreeNode* root) {
        if(!root)return true;
        return check(root->left, root->right);
    }
};
```