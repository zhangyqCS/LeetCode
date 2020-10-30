### 剪绳子

---

#### 1. 题意

&emsp;&emsp;给你一根长度为 n 的绳子，请把绳子剪成整数长度的 m 段（m、n都是整数，n>1并且m>1），每段绳子的长度记为 k[0],k[1]...k[m - 1] 。请问 k[0]*k[1]*...*k[m - 1] 可能的最大乘积是多少？例如，当绳子的长度是8时，我们把它剪成长度分别为2、3、3的三段，此时得到的最大乘积是18。

&emsp;&emsp;答案需要取模 1e9+7（1000000007），如计算初始结果为：1000000008，请返回 1。


#### 2. 思路

- **贪心**：尽量取长度为$3$的子段

#### 3. Code

```
class Solution {
    int mod = 1e9+7;
public:
    int cuttingRope(int n) {
        if(n <=3)return n-1;
        if(n == 4)return 4;

        long long res = 1;
        while(n > 4){
            res = (res * 3)%mod;
            n -= 3;
        }
        return (res*n)%mod;
    }
};
```