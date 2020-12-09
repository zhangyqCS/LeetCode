### 不用加减乘除做加法

---

#### 1. 题意

&emsp;&emsp;写一个函数，求两个整数之和，要求在函数体内不得使用 “+”、“-”、“*”、“/” 四则运算符号

#### 2. 思路

- **位运算**：[参考题解](https://leetcode-cn.com/problems/bu-yong-jia-jian-cheng-chu-zuo-jia-fa-lcof/solution/mian-shi-ti-65-bu-yong-jia-jian-cheng-chu-zuo-ji-7/)

#### 3. Code

```
class Solution {
public:
    int add(int a, int b) {
        // 避免出现 负数左移 操作，否则报错
        int tmp = ~(1 << 31);
        while(b != 0){
            int c = (a & b & tmp) << 1;
            a = a ^ b;
            b = c;
        }
        return a;
    }
};
```