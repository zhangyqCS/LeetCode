### 左旋转字符串

---

#### 1. 题意

字符串的左旋转操作是把字符串前面的若干个字符转移到字符串的尾部。请定义一个函数实现字符串左旋转操作的功能。比如，输入字符串"abcdefg"和数字2，该函数将返回左旋转两位得到的结果"cdefgab"

#### 2. 思路

- **遍历**

#### 3. Code

```
class Solution {
public:
    string reverseLeftWords(string s, int n) {
        string res = "";
        for(int i=n; i<s.size(); i++)res += s[i];
        for(int i=0; i<n; i++)res += s[i];

        return res;
    }
};
```