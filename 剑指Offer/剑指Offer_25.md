### 合并两个排序的链表

---

#### 1. 题意

&emsp;&emsp;输入两个递增排序的链表，合并这两个链表并使新链表中的节点仍然是递增排序的

#### 2. 思路

**Merge**

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
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
        ListNode* body = new ListNode(-1);
        ListNode* res = body;

        while(l1 != NULL && l2 !=NULL){
            if(l1->val < l2->val){ body->next = l1; l1 = l1->next; }
            else{
                body->next = l2;
                l2 = l2->next;
            }
            body = body->next;
        }

        if(l1 != NULL)body->next = l1;
        else
            body->next = l2;
        return res->next;
    }
};
```