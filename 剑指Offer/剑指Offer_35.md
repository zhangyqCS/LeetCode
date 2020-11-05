### 复杂链表的复制

---

#### 1. 题意

&emsp;&emsp;请实现 copyRandomList 函数，复制一个复杂链表。在复杂链表中，每个节点除了有一个 next 指针指向下一个节点，还有一个 random 指针指向链表中的任意节点或者 null

#### 2. 思路

**vector存储原链表，再根据 idx 复制**

#### 3. Code

```
/*
// Definition for a Node.
class Node {
public:
    int val;
    Node* next;
    Node* random;
    
    Node(int _val) {
        val = _val;
        next = NULL;
        random = NULL;
    }
};
*/
class Solution {
public:
    int getIdx(vector<Node*>nodes, Node* t){
        for(int i=0; i<nodes.size(); i++){
            if(nodes[i] == t){ return i; }
        }
        return -1;
    }

    Node* copyRandomList(Node* head) {
        if(head == NULL)return NULL;

        vector<Node*>nodes;
        vector<Node*>res;
        vector<int>rand;
        Node* tmp = head;        
        
        while(tmp){
            nodes.push_back(tmp);
            Node* cur_node = new Node(tmp->val);
            res.push_back(cur_node);
            tmp = tmp->next;
        }

        int i=0;
        while(head){
            int idx = getIdx(nodes, head->random);

            if(idx != -1){ res[i]->random = res[idx]; }
            head = head->next;
            i++;
        }
        
        for(int i=0; i<res.size()-1; i++){
            res[i]->next = res[i+1];
        }
        return res[0];
    }
};
```