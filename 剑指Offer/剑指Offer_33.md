### 二叉搜索树的后序遍历序列

---

#### 1. 题意

&emsp;&emsp;请输入一个整数数组，判断该数组是不是某二叉搜索树的后序遍历结果。如果是则返回 true，否则返回 false。假设输入的数组的任意两个数字都互不相同

#### 2. 思路

**将数组分为左右两部分，再递归**

#### 3. Code

```
class Solution {
public:
    bool verifyPostorder(vector<int>& postorder) {
        if(!postorder.size())return true;

        vector<int>left, right;
        int len = postorder.size();
        int i=0;
        // 左子树，数值全部小于根节点
        while(i < len-1 && postorder[i] < postorder[len-1]){
            left.push_back(postorder[i]);
            i++;
        }
        // 右子树，数值全部大于根节点
        while(i < len-1 && postorder[i] > postorder[len-1]){
            right.push_back(postorder[i]);
            i++;
        }
        // 乱序
        if(i != len-1)return false;
        else
            return (verifyPostorder(left) && verifyPostorder(right));
    }
};
```