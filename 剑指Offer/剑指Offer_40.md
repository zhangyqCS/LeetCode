### 最小的k个数

---

#### 1. 题意

&emsp;&emsp;输入整数数组 arr ，找出其中最小的 k 个数。例如，输入4、5、1、6、2、7、3、8这8个数字，则最小的4个数字是1、2、3、4

#### 2. 思路

- **sort**

#### 3. Code

```
class Solution {
public:
    vector<int> getLeastNumbers(vector<int>& arr, int k) {
        if(!arr.size())return {};

        vector<int>res;
        sort(arr.begin(), arr.end());

        for(int i=0 ;i<k; i++)res.push_back(arr[i]);
        return res;
    }
};
```