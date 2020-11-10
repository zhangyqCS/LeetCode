### 数据流中的中位数

---

#### 1. 题意

&emsp;&emsp;如何得到一个数据流中的中位数？如果从数据流中读出奇数个数值，那么中位数就是所有数值排序之后位于中间的数值。如果从数据流中读出偶数个数值，那么中位数就是所有数值排序之后中间两个数的平均值，[原题链接](https://leetcode-cn.com/problems/shu-ju-liu-zhong-de-zhong-wei-shu-lcof/)

#### 2. 思路

- **动态维护两个堆**：[参考题解](https://leetcode-cn.com/problems/shu-ju-liu-zhong-de-zhong-wei-shu-lcof/solution/zi-jie-ti-ku-jian-41-kun-nan-shu-ju-liu-zhong-de-z/)

#### 3. Code

```
class MedianFinder {
public:
    priority_queue< int, vector<int>, greater<int> >minHeap;
    priority_queue< int, vector<int>, less<int> >maxHeap;
    /** initialize your data structure here. */
    MedianFinder() {

    }
    
    void addNum(int num) {
        if(minHeap.size() == maxHeap.size()){
            maxHeap.push(num);
            minHeap.push(maxHeap.top());
            maxHeap.pop();
        }else{
            minHeap.push(num);
            maxHeap.push(minHeap.top());
            minHeap.pop();
        }
    }
    
    double findMedian() {
        double res;

        if(minHeap.size() == maxHeap.size()){
            res = (double)(minHeap.top() + maxHeap.top())/2;
        }else{
            res = (double)minHeap.top();
        }
        return res;
    }
};

/**
 * Your MedianFinder object will be instantiated and called as such:
 * MedianFinder* obj = new MedianFinder();
 * obj->addNum(num);
 * double param_2 = obj->findMedian();
 */
```