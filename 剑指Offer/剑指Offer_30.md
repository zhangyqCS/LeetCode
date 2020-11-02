### 包含min函数的栈

---

#### 1. 题意

&emsp;&emsp;输定义栈的数据结构，请在该类型中实现一个能够得到栈的最小元素的 min 函数在该栈中，调用 min、push 及 pop 的时间复杂度都是 O(1)

#### 2. 思路

**辅助栈，使其栈顶为当前最小值，且元素个数与数据栈相等**

#### 3. Code

```
class MinStack {
    stack<int>data, help;
public:
    /** initialize your data structure here. */
    MinStack() {
    
    }
    
    void push(int x) {
        data.push(x);
        if(help.empty() || x <= help.top())help.push(x);
        if(x > help.top()){
            int tmp = help.top();
            help.push(tmp);
        }
    }
    
    void pop() {
        if(!data.empty() && !help.empty()){
            data.pop();
            help.pop();
        }
    }
    
    int top() {
        return data.top();
    }
    
    int min() {
        return help.top();
    }
};

/**
 * Your MinStack object will be instantiated and called as such:
 * MinStack* obj = new MinStack();
 * obj->push(x);
 * obj->pop();
 * int param_3 = obj->top();
 * int param_4 = obj->min();
 */
```