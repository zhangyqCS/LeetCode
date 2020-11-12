### 在排序数组中查找数字-1

---

#### 1. 题意

统计一个数字在排序数组中出现的次数

#### 2. 思路

- **遍历**

#### 3. Code

```
class Solution {
public:
    int search(vector<int>& nums, int target) {
        if(!nums.size())return 0;

        int idx = 0, res = 0;
        while(idx < nums.size() && nums[idx] < target){ idx += 1; }
        while(idx < nums.size() && nums[idx] == target){ res += 1; idx += 1; }

        return res;
    }
};
```