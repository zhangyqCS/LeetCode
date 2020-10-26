### 圆圈中最后剩下的数字

---

#### 1. 题意

&emsp;&emsp;$[0,1,...,n-1]$ 这$n$个数字排成一个圆圈，从数字0开始，每次从这个圆圈里删除第m个数，求出这个圆圈里剩下的最后一个数字。(例如，$[0、1、2、3、4]$这5个数字组成一个圆圈，从数字0开始每次删除第3个数字，则删除的前4个数字依次是2、0、4、1，因此最后剩下的数字是3)

&emsp;&emsp;**约瑟夫环**

#### 2. 思路

<div align=center><img src="https://tva3.sinaimg.cn/large/006Ahf5Fly1gk31xdm4kcj30i60ak3zh.jpg"></div>
<div align=center>图1</div>

<div align=center><img src="https://tvax3.sinaimg.cn/large/006Ahf5Fly1gk320j2kh5j30gy098dhd.jpg"></div>
<div align=center>图2</div>

$$F(n, m) = \begin{cases}
0 & n=1 \\
[F(n-1, m)+ m] \% n & n > 1
\end{cases}$$

[题解来源](https://leetcode-cn.com/problems/yuan-quan-zhong-zui-hou-sheng-xia-de-shu-zi-lcof/solution/huan-ge-jiao-du-ju-li-jie-jue-yue-se-fu-huan-by-as/)

#### 3. Code

```
class Solution {
public:
    int F(int n, int m) {
        if(n == 0)return 0;
        else
            return (F(n-1, m) + m)%n;
    }
    int lastRemaining(int n, int m) {
        return F(n,m);
    }
};
```