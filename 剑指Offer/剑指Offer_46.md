### 把数字翻译成字符串

---

#### 1. 题意

&emsp;&emsp;给定一个数字，我们按照如下规则把它翻译为字符串：0 翻译成 “a” ，1 翻译成 “b”，……，11 翻译成 “l”，……，25 翻译成 “z”。一个数字可能有多个翻译。请编程实现一个函数，用来计算一个数字有多少种不同的翻译方法

#### 2. 思路

- **DP+递归**

#### 3. Code

```
class Solution {
public:
    int translateNum(int num) {
        if(num < 10)return 1;
        if(10 <= num && num <= 25)return 2;

        int mod = num % 100;

        if(10 <= mod && mod <= 25){
            return (translateNum(num / 100) + translateNum(num / 10));
        }else{
            return translateNum(num / 10);
        }
    }
};
```