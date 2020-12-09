### 构建乘积数组

---

#### 1. 题意

&emsp;&emsp;给定一个数组 A[0,1,…,n-1]，请构建一个数组 B[0,1,…,n-1]，其中 B 中的元素 B[i]=A[0]×A[1]×…×A[i-1]×A[i+1]×…×A[n-1]。不能使用除法

#### 2. 思路

- **遍历**：[参考题解](https://leetcode-cn.com/problems/gou-jian-cheng-ji-shu-zu-lcof/solution/mian-shi-ti-66-gou-jian-cheng-ji-shu-zu-biao-ge-fe/)

<div align=center><img src="https://tva3.sinaimg.cn/large/006Ahf5Fly1gks8kg4bsuj30e30amdgl.jpg"></div>
<div align=center>图 1</div>

#### 3. Code

```
class Solution {
public:
    vector<int> constructArr(vector<int>& a) {
        if(!a.size())return {};

        vector<int> res(a.size(), 1);
        int left = 1, right = 1; // 左下角+右上角

        for(int i=0; i<a.size(); i++){
            res[i] *= left;
            left *= a[i];

            res[a.size()-i-1] *= right;
            right *= a[a.size()-i-1];
        }
        return res;
    }
};
```