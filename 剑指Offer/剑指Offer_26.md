### 数的子结构

---

#### 1. 题意

&emsp;&emsp;输入两棵二叉树A和B，判断B是不是A的子结构(约定空树不是任意一个树的子结构)。B是A的子结构， 即 A中有出现和B相同的结构和节点值

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
    bool check(TreeNode* A, TreeNode* B){
        if(!B)return true;
        if(!A || A->val != B->val)return false;
        return (check(A->left, B->left) && check(A->right, B->right));
    }

    bool isSubStructure(TreeNode* A, TreeNode* B) {
        if(!A || !B)return false;
        bool res = false;
        if(A->val == B->val){ res = check(A, B); }
        if(!res)res = isSubStructure(A->left, B);
        if(!res)res = isSubStructure(A->right, B);
        return res;
    }
};
```