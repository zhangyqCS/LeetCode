### 0~n-1中缺失的数字

---

#### 1. 题意

一个长度为n-1的递增排序数组中的所有数字都是唯一的，并且每个数字都在范围0～n-1之内。在范围0～n-1内的n个数字中有且只有一个数字不在该数组中，请找出这个数字

#### 2. 思路

- **遍历**

#### 3. Code

```
class Solution {
public:
    int missingNumber(vector<int>& nums) {
        int res = -1;
        for(int i=0; i<nums.size(); i++){
            if(nums[i] != i){
                res = i;
                break;
            }
        }
        if(res == -1)res = nums.size();
        return res;
    }
};
```