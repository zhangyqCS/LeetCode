### 青蛙跳台阶问题

---

#### 1. 题意

&emsp;&emsp;一只青蛙一次可以跳上1级台阶，也可以跳上2级台阶。求该青蛙跳上一个 n 级的台阶总共有多少种跳法？

#### 2. 思路

- **DP**，$F(n) = F(n-1) + F(n-2)$

#### 3. Code

```
class Solution {
public:
    int numWays(int n) {
        int mod = 1e9+7;
        int res[105];
        res[0] = 1; res[1] = 1;

        for(int i=2; i<=n; i++){ res[i] = (res[i-1]%mod+ res[i-2]%mod)%mod; }
        return res[n]%mod;
    }
};
```