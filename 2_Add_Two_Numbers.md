##[2 Add Two Numbers](https://leetcode.com/problems/add-two-numbers/)
```cpp
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
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
       ListNode * root = NULL;
       ListNode *p = NULL;
       int temp = 0;
       for(;l1!=NULL||l2!=NULL;){
           if(l1!=NULL)temp += l1->val;
           if(l2!=NULL)temp += l2->val;
           ListNode *tp = new ListNode(temp%10);
           temp /= 10;
           if(p==NULL)p = root = tp;
           else p->next = tp;
           p = tp;
           if(l1!=NULL)l1=l1->next;
           if(l2!=NULL)l2=l2->next;
       }
       if(temp!=0){
           p->next = new ListNode(temp);
       }
       return root;
    }
};
```
