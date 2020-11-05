### 序列化二叉树

---

#### 1. 题意

&emsp;&emsp;请实现两个函数，分别用来序列化和反序列化二叉树

[原题链接](https://leetcode-cn.com/problems/xu-lie-hua-er-cha-shu-lcof/)

#### 2. 思路

- **队列，逐层编码+解码**
- **Tips**：int -> string: to_string(); string -> int: stoi();

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
class Codec {
public:
    const int INF = 0x3f3f3f3f;
    string Vec2String(vector<int> &s){
        if(!s.size())return "[]";
        string res = "[";
        
        for(int i=0; i<s.size()-1; i++){
            if(s[i] != INF)res += to_string(s[i])+",";
            else
                res += "null,";
        }

        if(s[s.size()-1] != INF)res += to_string(s[s.size()-1])+"]";
        else
            res += "null]";
        return res;
    }

    vector<int> String2Vec(string s){
        int idx = 1;
        string tmp = "";
        vector<int>res;
        while(idx < s.length()){
            while(s[idx] != ',' && s[idx] != ']'){
                tmp += s[idx];
                idx += 1;
            }
            
            if(tmp == "null"){
                res.push_back(INF);
            }else{
                int val = stoi(tmp);
                res.push_back(val);
            }
            tmp = "";
            idx += 1;
        }
        return res;
    }
    // Encodes a tree to a single string.
    string serialize(TreeNode* root) {
        vector<int>vec;
        if(!root)return Vec2String(vec);

        queue<TreeNode*>Q;
        vec.push_back(root->val);
        Q.push(root);
        
        while(!Q.empty()){
            TreeNode* cur_node = Q.front();
            Q.pop();
            
            if(cur_node->left == NULL){ vec.push_back(INF); }
            else{
                vec.push_back(cur_node->left->val);
                Q.push(cur_node->left);
            }

            if(cur_node->right == NULL){ vec.push_back(INF); }
            else{
                vec.push_back(cur_node->right->val);
                Q.push(cur_node->right);
            }
        }
        // 删除多余的 null 节点
        while(vec[vec.size()-1] == INF){ vec.pop_back(); }
        return Vec2String(vec);
    }

    // Decodes your encoded data to tree.
    TreeNode* deserialize(string data) {
        if(data.length() == 2)return NULL;

        vector<int>vec = String2Vec(data);
        
        TreeNode* root = new TreeNode(vec[0]);
        int idx = 1;
        queue<TreeNode*>Q;
        Q.push(root);

        while(!Q.empty()){
            TreeNode* cur_node = Q.front();
            Q.pop();

            // 左子树
            if(idx < vec.size() && vec[idx] != INF){
                TreeNode* l_node = new TreeNode(vec[idx]);
                cur_node->left = l_node;
                Q.push(l_node);
                idx += 1;
            }else{
                idx += 1;
            }
            // 右子树
            if(idx < vec.size() && vec[idx] != INF){
                TreeNode* r_node = new TreeNode(vec[idx]);
                cur_node->right = r_node;
                Q.push(r_node);
                idx += 1;
            }else{
                idx += 1;
            }
        }
        return root;
    }
};

// Your Codec object will be instantiated and called as such:
// Codec codec;
// codec.deserialize(codec.serialize(root));
```