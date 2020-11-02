### 从上到下打印二叉树——3

---

#### 1. 题意

&emsp;&emsp;请实现一个函数按照之字形顺序打印二叉树，即第一行按照从左到右的顺序打印，第二层按照从右到左的顺序打印，第三行再按照从左到右的顺序打印，其他行以此类推

#### 2. 思路

**队列+pair+翻转vector**

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
        for(int i=0; i<res.size(); i++){
            if(i & 1){ reverse(res[i].begin(), res[i].end()); }
        }
        
        return res;
    }
};
```