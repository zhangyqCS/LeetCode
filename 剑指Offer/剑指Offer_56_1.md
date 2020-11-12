### 数组中数字出现的次数

---

#### 1. 题意

一个整型数组 nums 里除两个数字之外，其他数字都出现了两次。请写程序找出这两个只出现一次的数字。要求时间复杂度是O(n)，空间复杂度是O(1)

#### 2. 思路

- **位运算**：[参考题解](https://leetcode-cn.com/problems/shu-zu-zhong-shu-zi-chu-xian-de-ci-shu-lcof/solution/shu-zu-zhong-shu-zi-chu-xian-de-ci-shu-by-leetcode/)

#### 3. Code

```
class Solution {
public:
    vector<int> singleNumbers(vector<int>& nums) {
        int tmp = 0;
        for(int i=0; i<nums.size(); i++)tmp = tmp ^ nums[i];

        int div = 1;
        while((tmp & div) == 0)div <<= 1;

        int res1=0, res2=0;
        for(int i=0; i<nums.size(); i++){
            if(div & nums[i]){ res1 = res1 ^ nums[i]; }
            else{
                res2 = res2 ^ nums[i];
            }
        }

        return vector<int>{res1, res2};
    }
};
```