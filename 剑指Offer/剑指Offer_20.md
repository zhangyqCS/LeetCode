### 表示数值的字符串

---

#### 1. 题意

&emsp;&emsp;请实现一个函数用来判断字符串是否表示数值（包括整数和小数）。例如，字符串"+100"、"5e2"、"-123"、"3.1416"、"-1E-16"、"0123"都表示数值，但"12e"、"1a3.14"、"1.2.3"、"+-5"及"12e+5.4"都不是

#### 2. 思路

**确定有限状态自动机模拟**：[题解参考](https://leetcode-cn.com/problems/biao-shi-shu-zhi-de-zi-fu-chuan-lcof/solution/biao-shi-shu-zhi-de-zi-fu-chuan-by-leetcode-soluti/)

<div align=center><img src="https://tva4.sinaimg.cn/large/006Ahf5Fly1gk9j7lwrunj30kw099761.jpg"></div>
<div align=center>图 1</div>

#### 3. Code

```
class Solution {
public:
    enum State {
        state_0,
        state_1,
        state_2,
        state_3,
        state_4,
        state_5,
        state_6,
        state_7,
        state_8,
        state_9,
    };

    enum CharType {
        char_num,
        char_exp,
        char_point,
        char_sign,
        char_space,
        char_undefine,
    };

    map<State, map<CharType, State> >transfer {
        {
            state_0, {
                {char_space, state_0},
                {char_sign, state_1},
                {char_point, state_9},
                {char_num, state_2},
            }
        },{
            state_1, {
                {char_num, state_2},
                {char_point, state_9},
            }
        },{
            state_2, {
                {char_num, state_2},
                {char_exp, state_5},
                {char_space, state_8},
                {char_point, state_3},
            }
        },{
            state_3, {
                {char_num, state_4},
                {char_exp, state_5},
                {char_space, state_8},
            }
        },{
            state_4, {
                {char_space, state_8},
                {char_num, state_4},
                {char_exp, state_5},
            }
        },{
            state_5, {
                {char_sign, state_6},
                {char_num, state_7},
            }
        },{
            state_6, {
                {char_num, state_7},
            }
        },{
            state_7, {
                {char_num, state_7},
                {char_space, state_8},
            }
        },{
            state_8, {
                {char_space ,state_8},
            }
        },{
            state_9, {
                {char_num, state_4},
            }
        }

    };
    
    CharType toCharType(char ch){
        if (ch >= '0' && ch <= '9') {
            return char_num;
        } else if (ch == 'e' || ch == 'E') {
            return char_exp;
        } else if (ch == '.') {
            return char_point;
        } else if (ch == '+' || ch == '-') {
            return char_sign;
        } else if (ch == ' ') {
            return char_space;
        } else {
            return char_undefine;
        }
    }

    bool isNumber(string s) {
        int len = s.length();
        State st = state_0;

        for (int i = 0; i < len; i++) {
            CharType typ = toCharType(s[i]);
            // 无对应的状态转移函数
            if (transfer[st].find(typ) == transfer[st].end()) {
                return false;
            } else {
                st = transfer[st][typ];
            }
        }
        return st == state_2 || st == state_3 || st == state_4 || st == state_7 || st == state_8;
    }
};
```