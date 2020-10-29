### 旋转数组的最小数字

---

#### 1. 题意

&emsp;&emsp;把一个数组最开始的若干个元素搬到数组的末尾，我们称之为数组的旋转。输入一个递增排序的数组的一个旋转，输出旋转数组的最小元素。例如，数组 [3,4,5,1,2] 为 [1,2,3,4,5] 的一个旋转，该数组的最小值为1

#### 2. 思路

- **遍历：$O(n)$**
- **二分：$O(\log n)$**

#### 3. Code

```
class Solution {
public:
    int minArray(vector<int>& numbers) {
        int left = 0, right = numbers.size()-1;

        while(left < right){
            int pivot = left + (right-left)/2;
            if(numbers[pivot] < numbers[right])right = pivot;
            else if(numbers[pivot] > numbers[right])left = pivot+1;
            else
                right--;
        }
        return numbers[left];
    }
};
```