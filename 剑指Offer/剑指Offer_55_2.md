### 平衡二叉树

---

#### 1. 题意

输入一棵二叉树的根节点，判断该树是不是平衡二叉树。如果某二叉树中任意节点的左右子树的深度相差不超过1，那么它就是一棵平衡二叉树

#### 2. 思路

- **递归求树的深度**

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
    bool flag = true;

    int getDepth(TreeNode* node){
        if(node == NULL)return 0;
        if(node->left == NULL && node->right == NULL)return 1;

        int depth_left = getDepth(node->left);
        int depth_right = getDepth(node->right);

        if(abs(depth_right - depth_left) > 1){ flag = false; }
        return max(depth_left, depth_right) + 1;
    }
    bool isBalanced(TreeNode* root) {
        if(root == NULL)return true;
        if(root->left == NULL && root->right == NULL)return true;
        flag = true;
        getDepth(root);
        return flag;
    }
};
```