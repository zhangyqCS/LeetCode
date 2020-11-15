### 求 1+2+...+n

---

#### 1. 题意

&emsp;&emsp;求 1+2+...+n ，要求不能使用乘除法、for、while、if、else、switch、case等关键字及条件判断语句（A?B:C）

#### 2. 思路

- **递归**

#### 3. Code

```
class Solution {
public:
    int sumNums(int n) {
        if(n == 1)return 1;
        return sumNums(n-1) + n;
    }
};
```