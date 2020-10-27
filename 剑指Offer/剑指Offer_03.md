### 数组中重复的数字

---

#### 1. 题意

&emsp;&emsp;在一个长度为 n 的数组 nums 里的所有数字都在 0～n-1 的范围内。数组中某些数字是重复的，但不知道有几个数字重复了，也不知道每个数字重复了几次，请找出数组中任意一个重复的数字。

#### 2. 思路

**哈希**

#### 3. Code

```
class Solution {
public:
    int findRepeatNumber(vector<int>& nums) {
        bool hash[100005];
        memset(hash, 0, sizeof(hash));
        int res = -1;

        for(int i=0; i<nums.size(); i++){
            if(hash[nums[i]]){
                res = nums[i];
                break;
            }else{
                hash[nums[i]] = 1;
            }
        }
        return res;
    }
};
```