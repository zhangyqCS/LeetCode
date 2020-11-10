### 数字序列中某一位的数字

---

#### 1. 题意

&emsp;&emsp;数字以0123456789101112131415…的格式序列化到一个字符序列中。在这个序列中，第5位（从下标0开始计数）是5，第13位是1，第19位是4，等等。请写一个函数，求任意第n位对应的数字

#### 2. 思路

- **找规律**：[参考题解](https://leetcode-cn.com/problems/shu-zi-xu-lie-zhong-mou-yi-wei-de-shu-zi-lcof/solution/mian-shi-ti-44-shu-zi-xu-lie-zhong-mou-yi-wei-de-6/)

#### 3. Code

```
class Solution {
public:
    int findNthDigit(int n) {
        if(n == 0)return 0;

        int digit = 1;
        long long start = 1;
        long long index_cnt = 9*digit*start;

        while(n > index_cnt){
            n -= index_cnt;
            digit += 1;
            start *= 10;
            index_cnt = 9*digit*start;
        }

        // 对应哪一个数字
        int num = start + (n-1)/digit;
        // 对应数字第几位
        int mod = (n-1) % digit;
        return (to_string(num)[mod]-'0');
    }
};
```