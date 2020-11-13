### 扑克牌中的顺子

---

#### 1. 题意

从扑克牌中随机抽5张牌，判断是不是一个顺子，即这5张牌是不是连续的。2～10为数字本身，A为1，J为11，Q为12，K为13，而大、小王为 0 ，可以看成任意数字。A 不能视为 14

#### 2. 思路

- **排序+遍历**：[参考题解](https://leetcode-cn.com/problems/bu-ke-pai-zhong-de-shun-zi-lcof/solution/mian-shi-ti-61-bu-ke-pai-zhong-de-shun-zi-ji-he-se/)

#### 3. Code

```
class Solution {
public:
    bool isStraight(vector<int>& nums) {
        if(!nums.size())return true;

        int cnt_0 = 0;
        sort(nums.begin(), nums.end());

        for(int i=0; i<nums.size()-1; i++){
            if(nums[i] == 0){ cnt_0 += 1; continue; }
            if(nums[i] == nums[i+1]){ return false; }
        }

        return nums[4] - nums[cnt_0] < 5;
    }
};
```