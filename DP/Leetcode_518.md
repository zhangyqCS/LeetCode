### 零钱兑换-2

---

#### 1. 题意

&emsp;&emsp;给定不同面额的硬币和一个总金额。写出函数来计算可以凑成总金额的硬币组合数。假设每一种面额的硬币有无限个

#### 2. 思路

- **完全背包DP**

#### 3. Code

```
// 简单方法
class Solution {
public:
    int change(int amount, vector<int>& coins) {
        if(!coins.size())return amount == 0;

        vector< vector<int> >dp(5005, vector<int>(5005, 0));

        // 初始化
        for(int i=0; i*coins[0] <= amount; i++)dp[1][i*coins[0]] = 1;
        dp[0][0] = 1;

        for(int i=2; i<=coins.size(); i++){
            for(int j=0; j<=amount; j++){
                for(int k=0; k*coins[i-1] <= j; k++){ dp[i][j] += dp[i-1][j-k*coins[i-1]]; }
            }
        }
        return dp[coins.size()][amount];
    }
};

// 优化
class Solution {
public:
    int change(int amount, vector<int>& coins) {
        if(!coins.size())return amount == 0;
        vector<int>dp(amount+1, 0);

        // 初始化
        for(int i=0; i*coins[0] <= amount; i++)dp[i*coins[0]] = 1;
        for(int i=2; i<= coins.size(); i++){
            for(int j=coins[i-1]; j<=amount; j++){
                dp[j] += dp[j-coins[i-1]];
            }
        }
        return dp[amount];
    }
};
```