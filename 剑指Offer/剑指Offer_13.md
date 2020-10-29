### 机器人的运动范围

---

#### 1. 题意

&emsp;&emsp;地上有一个m行n列的方格，从坐标 [0,0] 到坐标 [m-1,n-1] 。一个机器人从坐标 [0, 0] 的格子开始移动，它每次可以向左、右、上、下移动一格（不能移动到方格外），也不能进入行坐标和列坐标的数位之和大于k的格子。例如，当k为18时，机器人能够进入方格 [35, 37] ，因为3+5+3+7=18。但它不能进入方格 [35, 38]，因为3+5+3+8=19。请问该机器人能够到达多少个格子？

#### 2. 思路

- **BFS**

#### 3. Code

```
class Solution {
    int matrix[105][105];
    int cnt=0;
public:
    int cal_sum(int a, int b){
        int res = 0;
        
        while(a != 0){
            res += a%10;
            a /= 10;
        }

        while(b !=0){
            res += b%10;
            b /= 10;
        }
        return res;
    }
    void init(){
        memset(matrix, 0, sizeof(matrix));
        cnt = 0;

        for(int i=0; i<105; i++){
            for(int j=0; j<105; j++)matrix[i][j] = cal_sum(i,j);
        }
    }
    bool isBound(int x, int y, int m, int n){
        return x < 0 || x >= m || y < 0 || y >= n;
    }

    int movingCount(int m, int n, int k) {
        init();
        queue< pair<int, int> >Q;
        matrix[0][0] = -1;
        cnt += 1;
        Q.push(make_pair(0,0));

        while(!Q.empty()){
            pair<int, int> u = Q.front();
            Q.pop();

            // 上
            if(!isBound(u.first-1, u.second, m, n) && matrix[u.first-1][u.second] != -1 && matrix[u.first-1][u.second] <= k){
                matrix[u.first-1][u.second] = -1;
                cnt += 1;
                Q.push(make_pair(u.first-1, u.second));
            }
            // 下
            if(!isBound(u.first+1, u.second, m, n) && matrix[u.first+1][u.second] != -1 && matrix[u.first+1][u.second] <= k){
                matrix[u.first+1][u.second] = -1;
                cnt += 1;
                Q.push(make_pair(u.first+1, u.second));
            }
            // 左
            if(!isBound(u.first, u.second-1, m, n) && matrix[u.first][u.second-1] != -1 && matrix[u.first][u.second-1] <= k){
                matrix[u.first][u.second-1] = -1;
                cnt += 1;
                Q.push(make_pair(u.first, u.second-1));
            }
            // 右
            if(!isBound(u.first, u.second+1, m, n) && matrix[u.first][u.second+1] != -1 && matrix[u.first][u.second+1] <=k){
                matrix[u.first][u.second+1] = -1;
                cnt += 1;
                Q.push(make_pair(u.first, u.second+1));
            }
        }
        return cnt;
    }
};
```