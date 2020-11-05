### 二叉搜索树与双向链表

---

#### 1. 题意

&emsp;&emsp;输入一棵二叉搜索树，将该二叉搜索树转换成一个排序的循环双向链表。要求不能创建任何新的节点，只能调整树中节点指针的指向

[原题链接](https://leetcode-cn.com/problems/er-cha-sou-suo-shu-yu-shuang-xiang-lian-biao-lcof/)

#### 2. 思路

**vector暂存中序遍历结果，再更新指针**

#### 3. Code

```
/*
// Definition for a Node.
class Node {
public:
    int val;
    Node* left;
    Node* right;

    Node() {}

    Node(int _val) {
        val = _val;
        left = NULL;
        right = NULL;
    }

    Node(int _val, Node* _left, Node* _right) {
        val = _val;
        left = _left;
        right = _right;
    }
};
*/
class Solution {
public:
    vector<Node*>ordered;
    
    void inOrder(Node* root){
        if(root == NULL)return;

        inOrder(root->left);
        ordered.push_back(root);
        inOrder(root->right);
    }

    Node* treeToDoublyList(Node* root) {
        if(!root)return NULL;
        ordered.clear();
        inOrder(root);

        for(int i=0; i<ordered.size(); i++){
            int pre_idx = (i-1+ordered.size()) % ordered.size();
            int next_idx = (i+1)%ordered.size();

            ordered[i]->left = ordered[pre_idx];
            ordered[i]->right = ordered[next_idx];
        }
        return ordered[0];
    }
};
```