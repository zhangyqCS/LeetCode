### 数组中数字出现的次数-2

---

#### 1. 题意

在一个数组 nums 中除一个数字只出现一次之外，其他数字都出现了三次。请找出那个只出现一次的数字

#### 2. 思路

- **位运算**：[参考题解](https://leetcode-cn.com/problems/shu-zu-zhong-shu-zi-chu-xian-de-ci-shu-ii-lcof/solution/mian-shi-ti-56-ii-shu-zu-zhong-shu-zi-chu-xian-d-4/)

<div align=center><img src = "https://tvax3.sinaimg.cn/large/006Ahf5Fly1gknlesusfnj30cn09kdge.jpg"></div>
<div align=center>图 1</div>

#### 3. Code

```
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        int res = 0;

        for(int i=0; i<32; i++){
            int cnt = 0;
            for(int j=0; j<nums.size(); j++){
                if(nums[j] & (1 << i))cnt += 1;
            }
            if(cnt % 3 != 0)res = res ^ (1 << i);
        }
        return res;
    }
};
```