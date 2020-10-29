### 二进制中1的个数

---

#### 1. 题意

&emsp;&emsp;请实现一个函数，输入一个整数，输出该数二进制表示中 1 的个数。例如，把 9 表示成二进制是 1001，有 2 位是 1。因此，如果输入 9，则该函数输出 2

#### 2. 思路

- **移位 + &**

#### 3. Code

```
class Solution {
//typedef unsigned int      uint32_t;
public:
    int hammingWeight(uint32_t n) {
        int res = 0;
        while(n){
            if(n & 1)res += 1;
            n = n >>1;
        }

        return res;
    }
};
```