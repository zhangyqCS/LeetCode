### 数值的整数次方

---

#### 1. 题意

&emsp;&emsp;实现函数double Power(double base, int exponent)，求base的exponent次方。不得使用库函数，同时不需要考虑大数问题

#### 2. 思路

- **快速幂(注意 int 范围)**

#### 3. Code

```
class Solution {
public:
    double qpow(double x, long long n){
        double res = 1.0;
        while(n){
            if(n & 1)res = res*x;
            n = n >> 1;
            x = x*x;
        }
        return res;
    }
    double myPow(double x, int n) {
        long long p = n;

        if(x == 1.0)return x;
        if(p>=0)return qpow(x,p);
        else
            return 1.0/qpow(x,-p);
    }
};
```