### 队列的最大值

---

#### 1. 题意

请定义一个队列并实现函数 max_value 得到队列里的最大值，要求函数max_value、push_back 和 pop_front 的均摊时间复杂度都是O(1)。若队列为空，pop_front 和 max_value 需要返回 -1

#### 2. 思路

- **双端队列**：[参考题解](https://leetcode-cn.com/problems/dui-lie-de-zui-da-zhi-lcof/solution/mian-shi-ti-59-ii-dui-lie-de-zui-da-zhi-by-leetcod/)

#### 3. Code

```
class MaxQueue {
public:
    queue<int>Q;
    deque<int>D;

    MaxQueue() {
        while(!Q.empty())Q.pop();
        while(!D.empty())D.pop_back();
    }
    
    int max_value() {
        if(D.empty())return -1;
        return D.front();
    }
    
    void push_back(int value) {
        while(!D.empty() && D.back() < value)D.pop_back();

        D.push_back(value);
        Q.push(value);
    }
    
    int pop_front() {
        if(Q.empty())return -1;

        int res = Q.front();
        Q.pop();
        
        if(!D.empty() && D.front() == res)D.pop_front();
        return res;
    }
};

/**
 * Your MaxQueue object will be instantiated and called as such:
 * MaxQueue* obj = new MaxQueue();
 * int param_1 = obj->max_value();
 * obj->push_back(value);
 * int param_3 = obj->pop_front();
 */
```