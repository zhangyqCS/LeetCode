### 1～n 整数中 1 出现的次数

---

#### 1. 题意

&emsp;&emsp;输入一个整数 n ，求1～n这n个整数的十进制表示中1出现的次数。例如，输入12，1～12这些整数中包含1 的数字有1、10、11和12，1一共出现了5次

#### 2. 思路

- **数位拆解**：[参考题解](https://leetcode-cn.com/problems/1nzheng-shu-zhong-1chu-xian-de-ci-shu-lcof/solution/mian-shi-ti-43-1n-zheng-shu-zhong-1-chu-xian-de-2/)

#### 3. Code

```
class Solution {
public:
    int countDigitOne(int n) {
        int high = n / 10;
        int cur = n % 10;
        int low = 0;
        long digit = 1;
        int res = 0;

        while( high != 0 || cur != 0){
            if(cur == 0){ res += high*digit; }
            else if(cur == 1){ res += high*digit+low+1; }
            else{ res += (high+1)*digit; }

            low = cur*digit + low;
            cur = high % 10;
            high = high / 10;
            digit = digit*10;
        }
        return res;
    }
};
```