### 从上到下打印二叉树

---

#### 1. 题意

&emsp;&emsp;从上到下打印出二叉树的每个节点，同一层的节点按照从左到右的顺序打印

#### 2. 思路

**队列**

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
    vector<int> levelOrder(TreeNode* root) {
        vector<int>res;
        if(!root)return res;

        queue<TreeNode*>Q;
        Q.push(root);
        
        while(!Q.empty()){
            TreeNode* cur_node = Q.front();
            Q.pop();
            res.push_back(cur_node->val);
            if(cur_node->left)Q.push(cur_node->left);
            if(cur_node->right)Q.push(cur_node->right);
        }
        return res;
    }
};
```