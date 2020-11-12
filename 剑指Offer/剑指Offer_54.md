### 二叉搜索树的第k大节点

---

#### 1. 题意

给定一棵二叉搜索树，请找出其中第k大的节点

#### 2. 思路

- **中序遍历**

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
    vector<int>nums;
    
    void inOrder(TreeNode* root){
        if(root == NULL)return;

        inOrder(root->left);
        nums.push_back(root->val);
        inOrder(root->right);
    }
    
    int kthLargest(TreeNode* root, int k) {
        inOrder(root);
        return nums[nums.size()-k];
    }
};
```