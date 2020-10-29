### 矩阵中的路径

---

#### 1. 题意

&emsp;&emsp;请设计一个函数，用来判断在一个矩阵中是否存在一条包含某字符串所有字符的路径。路径可以从矩阵中的任意一格开始，每一步可以在矩阵中向左、右、上、下移动一格。如果一条路径经过了矩阵的某一格，那么该路径不能再次进入该格子

#### 2. 思路

- **DFS**

#### 3. Code

```
class Solution {
    bool flag = false;
public:
    bool isBound(vector<vector<char>>& board, int i, int j){
        return i<0 || i>=board.size() || j<0 || j>=board[0].size();
    }

    void DFS(vector<vector<char>>& board, string word, int i, int j, int cur_idx){
        if(cur_idx == word.length()-1){flag = true;}

        cur_idx += 1;
        //上移
        if(!isBound(board, i-1, j) && board[i-1][j] != '$' && board[i-1][j] == word[cur_idx]) {
            board[i-1][j] = '$';
            DFS(board, word, i-1, j, cur_idx);
            board[i-1][j] = word[cur_idx];

            if(flag)return;
        }
        //下移
        if(!isBound(board, i+1, j) && board[i+1][j] != '$' && board[i+1][j] == word[cur_idx]) {
            board[i+1][j] = '$';
            DFS(board, word, i+1, j, cur_idx);
            board[i+1][j] = word[cur_idx];
            
            if(flag)return;
        }
        //左移
        if(!isBound(board, i, j-1) && board[i][j-1] != '$' && board[i][j-1] == word[cur_idx]) {
            board[i][j-1] = '$';
            DFS(board, word, i, j-1, cur_idx);
            board[i][j-1] = word[cur_idx];
            
            if(flag)return;
        }
        //右移
        if(!isBound(board, i, j+1) && board[i][j+1] != '$' && board[i][j+1] == word[cur_idx]) {
            board[i][j+1] = '$';
            DFS(board, word, i, j+1, cur_idx);
            board[i][j+1] = word[cur_idx];

            if(flag)return;
        }
        return;
    }

    bool exist(vector<vector<char>>& board, string word) {
        if(!board.size())return false;    
        
        for(int i=0; i<board.size(); i++){
            for(int j=0; j<board[0].size(); j++){
                if(board[i][j] == word[0]){
                    board[i][j] = '$';
                    DFS(board, word, i, j, 0);
                    board[i][j] = word[0];

                    if(flag)break;
                }
            }
        }
        return flag;
    }
};
```