### 打家劫舍-2

---

#### 1. 题意

&emsp;&emsp;你是一个专业的小偷，计划偷窃沿街的房屋，每间房内都藏有一定的现金。这个地方所有的房屋都 **围成一圈** ，这意味着第一个房屋和最后一个房屋是紧挨着的。同时，相邻的房屋装有相互连通的防盗系统，如果两间相邻的房屋在同一晚上被小偷闯入，系统会自动报警 。

给定一个代表每个房屋存放金额的非负整数数组，计算你 在不触动警报装置的情况下 ，能够偷窃到的最高金额

#### 2. 思路

- **拆分成两个子问题DP**：第1个和最后一个房屋不能同时抢劫。[参考题解](https://leetcode-cn.com/problems/house-robber-ii/solution/213-da-jia-jie-she-iidong-tai-gui-hua-jie-gou-hua-/)

#### 3. Code

```
class Solution {
public:
    int rob(vector<int>& nums) {
        if(nums.size() == 1)return nums[0];
        
        vector<int>dp1(nums.size()+1, 0); // 不抢第一个
        vector<int>dp2(nums.size()+1, 0); // 不抢最后一个

        dp1[2] = nums[1];
        dp2[1] = nums[0];

        for(int i=3; i<=nums.size(); i++){
            dp1[i] = max(dp1[i-2] + nums[i-1], dp1[i-1]);
        }

        for(int i=2; i<nums.size(); i++){
            dp2[i] = max(dp2[i-2] + nums[i-1], dp2[i-1]);
        }

        return max(dp1[nums.size()], dp2[nums.size()-1]);
    }
};
```