### 两个链表的第一个公共节点

---

#### 1. 题意

输入两个链表，找出它们的第一个公共节点。[原题链接](https://leetcode-cn.com/problems/liang-ge-lian-biao-de-di-yi-ge-gong-gong-jie-dian-lcof/)

#### 2. 思路

- **循环双指针**：[参考题解](https://leetcode-cn.com/problems/liang-ge-lian-biao-de-di-yi-ge-gong-gong-jie-dian-lcof/solution/shuang-zhi-zhen-fa-lang-man-xiang-yu-by-ml-zimingm/)

#### 3. Code

```
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        ListNode* node1 = headA;
        ListNode* node2 = headB;

        while(node1 != node2){
            node1 = node1 == NULL ? headB : node1->next;
            node2 = node2 == NULL ? headA : node2->next;
        }
        return node1;
    }
};
```