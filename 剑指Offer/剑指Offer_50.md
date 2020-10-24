### 第一个只出现一次的字符

---

#### 1. 题意

在字符串 s 中找出第一个只出现一次的字符，若没有则返回 单空格(s只包括小写字母)

#### 2. 思路
哈希

#### 3. Code

```
class Solution {
public:
    char firstUniqChar(string s) {
        int hash[30];
        char res = ' ';

        memset(hash, 0, sizeof(hash));

        for(int i=0; i<s.length(); i++)hash[s[i]-'a']++;

        for(int i=0; i<s.length(); i++){
            if(hash[s[i]-'a'] == 1){
                res = s[i];
                break;
            }
        }
        return res;
    }
};
```