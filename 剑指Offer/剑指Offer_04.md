### 二维数组中的查找

---

#### 1. 题意

&emsp;&emsp;在一个 n * m 的二维数组中，每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。

#### 2. 思路

- **逐行二分查找：$O(n \log m)$**
- **类似二叉搜索树：$O(n+m)$**

<div align=center><img src="https://tvax4.sinaimg.cn/large/006Ahf5Fly1gk3q2y1tllj30cs09odgj.jpg"></div>
<div align=center>图1</div>

[题解来源](https://leetcode-cn.com/problems/er-wei-shu-zu-zhong-de-cha-zhao-lcof/solution/mian-shi-ti-04-er-wei-shu-zu-zhong-de-cha-zhao-zuo/)

#### 3. Code

```
class Solution {
public:
    bool findNumberIn2DArray(vector<vector<int>>& matrix, int target) {
        if(matrix.size() == 0)return false;

        int n = matrix.size()-1;
        int m = matrix[0].size()-1;

        bool flag = false;
        int i=n, j=0; //左下角

        while(true){
            if(i<0 || j>m)break;

            if(matrix[i][j] > target){ i--; }
            else if(matrix[i][j] < target){ j++; }
            else{
                flag = true;
                break;
            }
        }
        return flag;
    }
};
```