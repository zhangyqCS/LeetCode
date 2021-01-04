### 队列的最大值

---

#### 1. 题意

把n个骰子扔在地上，所有骰子朝上一面的点数之和为s。输入n，打印出s的所有可能的值出现的概率。你需要用一个浮点数数组返回答案，其中第 i 个元素代表这 n 个骰子所能掷出的点数集合中第 i 小的那个的概率。

#### 2. 思路

- **DP**：[参考题解](https://leetcode-cn.com/problems/nge-tou-zi-de-dian-shu-lcof/solution/nge-tou-zi-de-dian-shu-dong-tai-gui-hua-ji-qi-yo-3/)

#### 3. Code

```
class Solution {
public:
    vector<double> dicesProbability(int n) {
        vector<double>res;
        int dp[12][100];
        memset(dp, 0, sizeof(dp));

        for(int i=1; i<=6; i++){ dp[1][i] = 1; }
        for(int i=2; i<=11; i++){
            // j i 枚骰子可能组成的点数
            for(int j=i; j<=6*i; j++){
                // k 最后一枚骰子的点数
                for(int k=1; k<=6; k++){
                    if(j - k <= 0)break;
                    dp[i][j] += dp[i-1][j-k];
                }
            }
        }

        for(int i=n; i<=6*n; i++){res.push_back(dp[n][i]*1.0/(double)pow(6,n)); }
        return res;
    }
};
```