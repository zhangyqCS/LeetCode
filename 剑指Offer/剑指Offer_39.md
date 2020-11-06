### 数组中出现次数超过一半的数字

---

#### 1. 题意

&emsp;&emsp;数组中有一个数字出现的次数超过数组长度的一半，请找出这个数字。你可以假设数组是非空的，并且给定的数组总是存在多数元素

#### 2. 思路

- **map**

#### 3. Code

```
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        map<int,int>mp;
        int res;

        for(int i=0; i<nums.size(); i++){
            if(mp.count(nums[i]) == 0)mp[nums[i]] = 0;
            
            mp[nums[i]] += 1;
            if(mp[nums[i]] > nums.size()/2){ res = nums[i]; break; }
        }

        return res;
    }
};
```