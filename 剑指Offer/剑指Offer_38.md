### 字符串的排列

---

#### 1. 题意

&emsp;&emsp;输入一个字符串，打印出该字符串中字符的所有排列。你可以以任意顺序返回这个字符串数组，但里面不能有重复元素

#### 2. 思路

- **DFS**

#### 3. Code

```
class Solution {
public:
    vector<string>res;
    bool visit[10];

    void DFS(string &cur_s, string s){
        if(cur_s.length() == s.length()){ res.push_back(cur_s); }

        for(int i=0; i<s.length(); i++){
            // 避免相同字符被放到同一位置多次
            if(i>0 && s[i-1] == s[i] && visit[i-1])continue;
            if(visit[i])continue;

            cur_s.push_back(s[i]);
            visit[i] = true;
            DFS(cur_s, s);
            cur_s.pop_back();
            visit[i] = false;
        }
    }

    vector<string> permutation(string s) {
        if(!s.size())return {};
        // 初始化
        res.clear();
        memset(visit, false, sizeof(visit));
        // 排序，保证 s 中相同字符相邻
        sort(s.begin(), s.end());
        string cur_s = "";
        DFS(cur_s, s);

        return res;
    }
};
```