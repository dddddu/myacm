思路挺简单的 就是写的时候注意空指针就行了 唯一需要注意的地方就是 最后两个相加大于0但是已经到
链表末尾了 这时候需要在后边新加入一个节点

```c++
class Solution {
public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        ListNode* t1;
        ListNode* t2;
        t1=l1;
        t2=l2;
        while(t1!=nullptr&&t2!=nullptr){
            t1->val=t1->val+t2->val;
            t2->val=t1->val;
            t1=t1->next;
            t2=t2->next;
        }
        if(t1==nullptr)
        {
            t1=l2;
            t2=l2;
        }else{
           t1=l1;
           t2=l1;
        }
        while(t2!=nullptr){
            if(t2->val>=10)
            {
                t2->val-=10;
                if(t2->next==nullptr)
                    t2->next=new ListNode(0);
                t2->next->val+=1;
            }
            
            t2=t2->next;
        }
        return t1;
    }
};
```