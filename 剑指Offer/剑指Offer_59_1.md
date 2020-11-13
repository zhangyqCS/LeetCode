### 滑动窗口的最大值

---

#### 1. 题意

给定一个数组 nums 和滑动窗口的大小 k，请找出所有滑动窗口里的最大值。[题目链接](https://leetcode-cn.com/problems/hua-dong-chuang-kou-de-zui-da-zhi-lcof/)

#### 2. 思路

- **暴力**

#### 3. Code

```
class Solution {
public:
    vector<int> maxSlidingWindow(vector<int>& nums, int k) {
        if(!nums.size())return {};
        vector<int>res;

        for(int i=0; i<=nums.size()-k; i++){
            int tmp = -0x3f3f3f3f;
            for(int j=0; j<k; j++){ tmp= max(tmp, nums[i+j]); }
            res.push_back(tmp);
        }

        return res;
    }
};
```