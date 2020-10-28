### 重建二叉树

---

#### 1. 题意

&emsp;&emsp;输入某二叉树的前序遍历和中序遍历的结果，请重建该二叉树。假设输入的前序遍历和中序遍历的结果中都不含重复的数字。

#### 2. 思路

递归，逐步构建左子树和右子树

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
    int getPos(vector<int>& vec, int T){
        for(int i=0; i<vec.size(); i++){
            if(vec[i] == T){ return i; }
        }
        return -1;
    }

    TreeNode* rebuild(vector<int>& preorder, vector<int>& inorder, int s1, int e1, int s2, int e2) {
        TreeNode* root = new TreeNode(preorder[s1]);
        int pos = getPos(inorder, preorder[s1]);

        if(pos != s2){ //左子树不为空
            root->left = rebuild(preorder, inorder,s1+1, s1+pos-s2, s2, pos-1);
        }
        if(pos != e2){ //右子树不为空
            root->right = rebuild(preorder, inorder,s1+pos-s2+1, e1, pos+1, e2);
        }
        return root;
    }
    TreeNode* buildTree(vector<int>& preorder, vector<int>& inorder) {
        if(preorder.size()){
            return rebuild(preorder, inorder, 0, preorder.size()-1, 0, preorder.size()-1);
        }else{
            return NULL;
        }
    }
};
```