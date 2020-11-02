### 翻转链表

---

#### 1. 题意

&emsp;&emsp;定义一个函数，输入一个链表的头节点，反转该链表并输出反转后链表的头节点

#### 2. 思路

**两个指针：pre_node, cur_node+遍历**

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
    ListNode* reverseList(ListNode* head) {
        ListNode* pre=NULL;
        ListNode* cur = head;
        while(cur != NULL){
            ListNode* tmp = cur->next;
            cur->next = pre;
            pre = cur;
            cur = tmp;
        }
        return pre;
    }
};
```