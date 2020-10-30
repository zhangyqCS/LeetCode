### 打印从1到最大的n位数

---

#### 1. 题意

&emsp;&emsp;输入数字 n，按顺序打印出从 1 到最大的 n 位十进制数。比如输入 3，则打印出 1、2、3 一直到最大的 3 位数 999

#### 2. 思路

- **1 ~ pow(10,n)枚举**

#### 3. Code

```
class Solution {
public:
    vector<int> printNumbers(int n) {
        vector<int> res;
        for(int i=1; i<pow(10,n); i++){ res.push_back(i); }
        return res;
    }
};
```