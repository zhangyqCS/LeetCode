### 斐波那契数列

---

#### 1. 题意

&emsp;&emsp;求斐波那契数列的第$n$项

#### 2. 思路

- $F(n) = F(n-1) + F(n-2)$

#### 3. Code

```
class Solution {
public:
    int fib(int n) {
        int mod = 1e9+7;
        int res[105];
        res[0] = 0; res[1] = 1;

        for(int i=2; i<=n; i++){ res[i] = (res[i-1]%mod+ res[i-2]%mod)%mod; }
        return res[n]%mod;
    }
};
```