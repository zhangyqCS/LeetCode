### 栈的压入、弹出序列

---

#### 1. 题意

&emsp;&emsp;输入两个整数序列，第一个序列表示栈的压入顺序，请判断第二个序列是否为该栈的弹出顺序。假设压入栈的所有数字均不相等。例如，序列 {1,2,3,4,5} 是某栈的压栈序列，序列 {4,5,3,2,1} 是该压栈序列对应的一个弹出序列，但 {4,3,5,1,2} 就不可能是该压栈序列的弹出序列

#### 2. 思路

**辅助栈模拟**：[参考题解](https://leetcode-cn.com/problems/zhan-de-ya-ru-dan-chu-xu-lie-lcof/solution/mian-shi-ti-31-zhan-de-ya-ru-dan-chu-xu-lie-mo-n-2/)

#### 3. Code

```
class Solution {
public:
    bool validateStackSequences(vector<int>& pushed, vector<int>& popped) {
        if(!pushed.size() && !popped.size())return true;

        stack<int>s;
        int idx = 0;
        for(int i=0; i<pushed.size(); i++){
            s.push(pushed[i]);
            
            while(!s.empty() && popped[idx] == s.top()){
                idx++;
                s.pop();
            }
        }
        return s.empty();
    }
};
```