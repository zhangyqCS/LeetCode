### 替换空格

---

#### 1. 题意

&emsp;&emsp;实现一个函数，把字符串 s 中的每个空格替换成"%20"。

#### 2. 思路

遍历，逐个替换

#### 3. Code

```
class Solution {
public:
    string replaceSpace(string s) {
        string res = "";

        for(int i=0; i<s.length(); i++){
            if(s[i] == ' '){
                res += "%20";
            }else{
                res += s[i];
            }
        }
        return res;
    }
};
```