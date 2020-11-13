### 和为 s 的连续正数序列

---

#### 1. 题意

输入一个正整数 target ，输出所有和为 target 的连续正整数序列（至少含有两个数）。序列内的数字由小到大排列，不同序列按照首个数字从小到大排列

#### 2. 思路

- **滑动窗口**：[参考题解](https://leetcode-cn.com/problems/he-wei-sde-lian-xu-zheng-shu-xu-lie-lcof/solution/shi-yao-shi-hua-dong-chuang-kou-yi-ji-ru-he-yong-h/)

#### 3. Code

```
class Solution {
public:
    vector<vector<int>> findContinuousSequence(int target) {
        int i = 1; //滑动窗口左边界
        int j = 1; //滑动窗口右边界
        int sum = 0;
        vector< vector<int> >res;

        while(i <= target/2){
            if(sum < target){
                sum += j;
                j += 1;
            }else if(sum > target){
                sum -= i;
                i += 1;
            }else{
                vector<int>tmp;
                for(int k=i; k<j; k++)tmp.push_back(k);
                res.push_back(tmp);

                sum -= i;
                i += 1;
            }
        }
        return res;
    }
};
```