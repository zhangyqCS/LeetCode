### 圆圈中最后剩下的数字

---

#### 1. 题意

求二叉树的深度

#### 2. 思路
DFS，递归求左右子树的深度，求max

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
    int DFS(TreeNode* n) {
        if(n == NULL)return 0;

        int l = DFS(n->left);
        int r = DFS(n->right);

        return max(l, r) + 1;
    }

    int maxDepth(TreeNode* root) {
        return DFS(root);
    }
};
```