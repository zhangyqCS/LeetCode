### 顺时针打印矩阵

---

#### 1. 题意

&emsp;&emsp;输入一个矩阵，按照从外向里以顺时针的顺序依次打印出每一个数字

#### 2. 思路

**模拟**

#### 3. Code

```
class Solution {
public:
    vector<int> spiralOrder(vector<vector<int>>& matrix) {
        vector<int>res;
        bool flag[105][105];
        memset(flag, false, sizeof(flag));

        if(!matrix.size())return res;
        int m = matrix.size(), n = matrix[0].size();
        // k 层数
        for(int k=0; k<=(min(m,n)-1)/2; k++){
            // 上
            for(int j=k; j<=n-1-k;j++){
                if(!flag[k][j]){ res.push_back(matrix[k][j]); flag[k][j] = true; }
            }
            // 右
            for(int i=k+1; i<=m-1-k; i++){
                if(!flag[i][n-1-k]){ res.push_back(matrix[i][n-1-k]); flag[i][n-1-k] = true; }
            }
            // 下
            for(int j=n-1-k-1; j>=k; j--){
                if(!flag[m-1-k][j]){ res.push_back(matrix[m-1-k][j]);flag[m-1-k][j] = true; }
            }
            // 左
            for(int i=m-1-k-1; i>=k+1; i--){
                if(!flag[i][k]){ res.push_back(matrix[i][k]);flag[i][k] = true; }
            }
        }
        return res;
    }
};
```