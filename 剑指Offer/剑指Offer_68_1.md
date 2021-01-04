### 二叉搜索树的最近公共祖先

---

#### 1. 题意

&emsp;&emsp;给定一个二叉搜索树, 找到该树中两个指定节点的最近公共祖先。

#### 2. 思路

- **BFS+递归**

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
    bool isChild(TreeNode* root, TreeNode* targ){
        if(root == targ)return true;
        bool flag = false;

        if(root->left != NULL)flag = flag || isChild(root->left, targ);
        if(root->right != NULL)flag = flag || isChild(root->right, targ);
        return flag;
    }

    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
        stack<TreeNode*>s;
        queue<TreeNode*>Q;
        Q.push(root);

        while(!Q.empty()){
            TreeNode* cur_node = Q.front();
            Q.pop();

            bool flag1 = isChild(cur_node, p);
            bool flag2 = isChild(cur_node, q);

            if(flag1 && flag2){ s.push(cur_node); }

            if(cur_node->left)Q.push(cur_node->left);
            if(cur_node->right)Q.push(cur_node->right);
        }

        return s.top();
    }
};
```