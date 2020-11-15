### 股票的最大利润

---

#### 1. 题意

&emsp;&emsp;假设把某股票的价格按照时间先后顺序存储在数组中，请问买卖该股票一次可能获得的最大利润是多少？

#### 2. 思路

- **DP? or 贪心遍历**

#### 3. Code

```
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        if(!prices.size())return 0;

        int res = 0, m = 0x3f3f3f3f;
        for(int i=0; i<prices.size(); i++){
            m = min(m, prices[i]);
            if(prices[i] - m > 0)res = max(res, prices[i]-m);
        }
        
        return res;
    }
};
```