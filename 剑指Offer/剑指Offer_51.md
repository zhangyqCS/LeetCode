### 数组中的逆序对

---

#### 1. 题意

在数组中的两个数字，如果前面一个数字大于后面的数字，则这两个数字组成一个逆序对。输入一个数组，求出这个数组中的逆序对的总数

#### 2. 思路

- **分治**

#### 3. Code

```
class Solution {
public:
    vector<int>sorted_nums;
    vector<int>tmp;
    
    int countReverse(int left, int right){
        if(right - left < 1)return 0;

        int mid = (right + left)/2;
        
        int res_left = countReverse(left, mid);
        int res_right = countReverse(mid+1, right);

        int res = 0; //横跨两边的逆序对数
        int idx1 = left, idx2 = mid+1;
        int idx_tmp = 0;

        while(idx1 <= mid && idx2 <= right){
            if(sorted_nums[idx1] > sorted_nums[idx2]){
                res += mid-idx1+1;
                tmp[idx_tmp++] = sorted_nums[idx2];
                idx2 += 1;
            }else{
                tmp[idx_tmp++] = sorted_nums[idx1];
                idx1 += 1;
            }
        }

        while(idx1 <= mid){ tmp[idx_tmp++] = sorted_nums[idx1]; idx1++; }
        while(idx2 <= right){ tmp[idx_tmp++] = sorted_nums[idx2]; idx2++; }
        for(int i=0; i<idx_tmp; i++){ sorted_nums[left+i] = tmp[i]; }
        
        return res + res_left + res_right;
    }

    int reversePairs(vector<int>& nums) {
        if(!nums.size())return 0;
        
        for(int i=0; i<nums.size(); i++){ sorted_nums.push_back(nums[i]); tmp.push_back(nums[i]); }
        return countReverse(0, nums.size()-1);
    }
};
```