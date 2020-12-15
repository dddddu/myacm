>测这道题目的时候发现leetcode的运行时间和内存消耗不准确度有点大 同样的代码都能跑不同的时间，归根到底还是数据量太小了

```c++
class Solution {
public:
    ListNode* rotateRight(ListNode* head, int k) {
       
        if(head==nullptr)
            return head;
        ListNode* t=head;
        int len=0;
        while(t->next!=nullptr){
            len++;
            t=t->next;
        }
        if(t!=nullptr)
            len++;
        t->next=head;
       

        k=k%len;
        k=len-k;
        for(int i=1;i<=k;i++){
            t=t->next;
        }
        head=t->next;
        t->next=nullptr;
        return head;
    }
};
```