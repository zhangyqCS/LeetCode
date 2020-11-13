### 翻转单词顺序

---

#### 1. 题意

输入一个英文句子，翻转句子中单词的顺序，但单词内字符的顺序不变。为简单起见，标点符号和普通字母一样处理。例如输入字符串"I am a student. "，则输出"student. a am I"

#### 2. 思路

- **遍历拆分**

#### 3. Code

```
class Solution {
public:
    string reverseWords(string s) {
        if(!s.size())return "";

        string res = "";
        vector<string>str;

        int i = 0;
        while(i < s.size()){
            if(s[i] != ' '){
                string tmp = "";
                while(i < s.size() && s[i] != ' '){ tmp += s[i]; i++; }
                str.push_back(tmp);
            }else{
                i += 1;
            }
        }

        if(str.size()){
            for(int j=str.size()-1; j>0; j--){ res += str[j] + ' '; }
            res += str[0];
        }


        return res;
    }
};
```