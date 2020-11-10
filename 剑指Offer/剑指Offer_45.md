### 把数组排成最小的数

---

#### 1. 题意

&emsp;&emsp;输入一个非负整数数组，把数组里所有数字拼接起来排成一个数，打印能拼接出的所有数字中最小的一个

#### 2. 思路

- **自定义优先级，对原数组进行排序**

#### 3. Code

```
class Solution {
public:
    static bool cmp(int num1, int num2){
        string str1 = to_string(num1) + to_string(num2);
        string str2 = to_string(num2) + to_string(num1);
        return str1.compare(str2) < 0;
    }

    string minNumber(vector<int>& nums) {
        sort(nums.begin(), nums.end(), cmp);
        string res = "";

        for(int i=0; i<nums.size(); i++){
            res += to_string(nums[i]);
        }
        return res;
    }
};
```