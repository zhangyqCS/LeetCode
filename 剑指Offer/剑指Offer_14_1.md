### 剪绳子

---

#### 1. 题意

&emsp;&emsp;给你一根长度为 n 的绳子，请把绳子剪成整数长度的 m 段（m、n都是整数，n>1并且m>1），每段绳子的长度记为 k[0],k[1]...k[m-1] 。请问 k[0]*k[1]*...*k[m-1] 可能的最大乘积是多少？例如，当绳子的长度是8时，我们把它剪成长度分别为2、3、3的三段，此时得到的最大乘积是18

#### 2. 思路

- **2维DP**：$dp[i][j]$表示绳子长度为$i$时，剪成$j$段的最大乘积，初始化$dp[i][2] = max j*(i-j)  [1 \leq j \leq i-1]$，假设最后一段长度为$k$，则状态转移方程为：$$dp[i][j] = \begin{cases}
dp[i][j-1] & k=0 \\
max(dp[i-k][j-1]*k) & otherwise
\end{cases}$$

- **1维DP**：$dp[i]$表示绳子长度为$i$时，剪成$m$段后的最大乘积(不 care $m$ 的值)，当$n \geq 4$时，若某一段的长度处于区间$[0,3]$内，则再分会导致乘积变小，此处需要特判

#### 3. Code

```
// 2维DP
class Solution {
public:
    int cuttingRope(int n) {
        int dp[60][60];
        memset(dp, 0, sizeof(dp));
        // 初始化
        for(int i=2; i<=n; i++){
            dp[i][2] = -1;
            for(int j=1; j<i; j++){ dp[i][2] = max(dp[i][2], j*(i-j)); }
        }

        for(int i=2; i<=n; i++){
            for(int j=3; j<=i; j++){
                for(int k=0; k<i; k++){
                    if(k == 0){ dp[i][j] = dp[i][j-1]; }
                    else{
                        dp[i][j] = max(dp[i][j], dp[i-k][j-1]*k);
                    }
                }
            }
        }
        int res = -1;
        for(int i=2; i<=n; i++)res = max(res, dp[n][i]);
        return res;
    }
};

// 1维DP
class Solution {
public:
    int cuttingRope(int n) {
        if(n <=3)return n-1;

        int dp[60];
        memset(dp, 0, sizeof(dp));
        // 初始化，特判
        dp[0] = 0;
        dp[1] = 1;
        dp[2] = 2;
        dp[3] = 3;

        for(int i=4; i<=n; i++){
            for(int k=1; k<=i/2; k++){
                dp[i] = max(dp[i], dp[i-k]*dp[k]);
            }
        }
        return dp[n];
    }
};
```