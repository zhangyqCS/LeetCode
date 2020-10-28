### 从尾到头打印链表

---

#### 1. 题意

&emsp;&emsp;输入一个链表的头节点，从尾到头反过来返回每个节点的值（用数组返回）。

#### 2. 思路

逐个遍历，再利用 reverse 翻转 vector<int>数组

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
    vector<int> reversePrint(ListNode* head) {
        vector<int> res;

        while(head != NULL){
            res.push_back(head->val);
            head = head->next;
        }
        reverse(res.begin(), res.end());
        return res;
    }
};
```