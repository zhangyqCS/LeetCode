### 调整数组顺序使奇数位于偶数前面

---

#### 1. 题意

&emsp;&emsp;输入一个整数数组，实现一个函数来调整该数组中数字的顺序，使得所有奇数位于数组的前半部分，所有偶数位于数组的后半部分

#### 2. 思路

**合并两个 vector\<int>**

#### 3. Code

```
class Solution {
public:
    vector<int> exchange(vector<int>& nums) {
        vector<int>res1, res2;
        for(int i=0; i<nums.size(); i++){
            if(nums[i] & 1)res1.push_back(nums[i]);
            else
                res2.push_back(nums[i]);
        }
        res1.insert(res1.end(), res2.begin(), res2.end());
        return res1;
    }
};
```