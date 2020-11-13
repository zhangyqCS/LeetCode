### 和为 s 的两个数字

---

#### 1. 题意

输入一个递增排序的数组和一个数字s，在数组中查找两个数，使得它们的和正好是s。如果有多对数字的和等于s，则输出任意一对即可

#### 2. 思路

- **哈希**

#### 3. Code

```
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        map<int, int>hash;
        int res1, res2;

        for(int i=0; i<nums.size(); i++){
            // hash[nums[i]] += 1;            
            if(nums[i] <= target && hash[target-nums[i]] != 0){
                res1 = nums[i];
                res2 = target - nums[i];
                break;
            }
            hash[nums[i]] += 1;
        }
        return vector<int>{res1, res2};
    }
};
```