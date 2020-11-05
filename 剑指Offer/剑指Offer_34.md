### 二叉树中和为某一值的路径

---

#### 1. 题意

&emsp;&emsp;输入一棵二叉树和一个整数，打印出二叉树中节点值的和为输入整数的所有路径。从树的根节点开始往下一直到叶节点所经过的节点形成一条路径

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
    vector<vector<int>> pathSum(TreeNode* root, int sum) {
        vector< vector<int> >res;
        if(!root)return res;
        
        if(root->left == NULL && root->right == NULL){
            if(root->val != sum)return res;
            else{
                res.push_back({});
                res[0].push_back(root->val);
                return res;
            }
        }

        vector< vector<int> >path_l = pathSum(root->left, sum-root->val);
        vector< vector<int> >path_r = pathSum(root->right, sum-root->val);

        if(path_l.size()){
            for(int i=0; i<path_l.size(); i++){
                res.push_back({});
                int idx = res.size();
                
                res[idx-1].push_back(root->val);
                res[idx-1].insert(res[idx-1].end(), path_l[i].begin(), path_l[i].end());
            }
        }

        if(path_r.size()){
            for(int i=0; i<path_r.size(); i++){
                res.push_back({});
                int idx = res.size();

                res[idx-1].push_back(root->val);
                res[idx-1].insert(res[idx-1].end(), path_r[i].begin(), path_r[i].end());
            }
        }

        return res;
    }
};
```