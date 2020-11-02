### 从上到下打印二叉树——2

---

#### 1. 题意

&emsp;&emsp;从上到下按层打印二叉树，同一层的节点按从左到右的顺序打印，每一层打印到一行

#### 2. 思路

**队列+pair**

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
    vector<vector<int>> levelOrder(TreeNode* root) {
        vector< vector<int> >res;
        if(!root)return res;

        queue< pair<TreeNode*, int> >Q;
        Q.push(make_pair(root, 0));
        
        while(!Q.empty()){
            pair<TreeNode*, int> u = Q.front();
            Q.pop();
            if(res.size() <= u.second){ res.push_back({}); }
            
            res[u.second].push_back(u.first->val);
            if(u.first->left)Q.push(make_pair(u.first->left, u.second+1));
            if(u.first->right)Q.push(make_pair(u.first->right, u.second+1));
        }
        return res;
    }
};
```