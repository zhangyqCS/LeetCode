### 删除链表的节点

---

#### 1. 题意

&emsp;&emsp;给定单向链表的头指针和一个要删除的节点的值，定义一个函数删除该节点，返回删除后的链表的头节点

#### 2. 思路

- **链表节点删除**

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
    ListNode* deleteNode(ListNode* head, int val) {
        if(val == head->val)return head->next;
        
        ListNode* pre_node = head;
        ListNode* cur_node = head->next;
        while(cur_node){
            if(cur_node->val == val){
                pre_node->next = cur_node->next;
                break;
            }
            pre_node = cur_node;
            cur_node = cur_node->next;
        }

        return head;
    }
};
```