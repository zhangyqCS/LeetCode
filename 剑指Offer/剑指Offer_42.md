### 连续子数组的最大和

---

#### 1. 题意

&emsp;&emsp;输入一个整型数组，数组中的一个或连续多个整数组成一个子数组。求所有子数组的和的最大值。要求时间复杂度为O(n)

#### 2. 思路

- **DP**

#### 3. Code

```
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int res = -0x3f3f3f3f;
        res = max(res, nums[0]);

        for(int i=1; i<nums.size(); i++){
            nums[i] = max(nums[i-1] + nums[i], nums[i]);
            res = max(res, nums[i]);
        }
        return res;
    }
};
```