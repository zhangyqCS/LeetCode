### 丑数

---

#### 1. 题意

&emsp;&emsp;我们把只包含质因子 2、3 和 5 的数称作丑数（Ugly Number）。求按从小到大的顺序的第 n 个丑数

#### 2. 思路

**堆(Tips：任一丑数均可由一个较小的丑数乘以质因子2、3、5产生)**

#### 3. Code

```
class Solution {
public:
    int nthUglyNumber(int n) {
        priority_queue< long, vector<long>, greater<long> >heap;
        map<long, bool>hash; // 标记 某一数字 是否已在 heap 内
        int cnt = 1;
        long cur_val;
        heap.push(1);

        while(!heap.empty() && cnt <= n){
            cur_val = heap.top();
            heap.pop();
            
            if(hash.count(cur_val*2) == 0){
                heap.push(cur_val*2);
                hash[cur_val*2] = true;
            }

            if(hash.count(cur_val*3) == 0){
                heap.push(cur_val*3);
                hash[cur_val*3] = true;
            }

            if(hash.count(cur_val*5) == 0){
                heap.push(cur_val*5);
                hash[cur_val*5] = true;
            }

            cnt += 1;
        }
        return cur_val;
    }
};
```