```
struct ListNode* addTwoNumbers(struct ListNode* l1, struct ListNode* l2) {
    struct ListNode *head = NULL, *tail = NULL;
    int carry = 0;
    while (l1 || l2) {
        int n1 = l1 ? l1->val : 0;
        int n2 = l2 ? l2->val : 0;//第6行和第7行可以省去l1 , l2 为空的情况
        int sum = n1 + n2 + carry;
        if (!head) {
            head = tail = malloc(sizeof(struct ListNode));
            tail->val = sum % 10;
            tail->next = NULL;
        } else {
            tail->next = malloc(sizeof(struct ListNode));
            tail->next->val = sum % 10;
            tail = tail->next;
            tail->next = NULL;
        }
        carry = sum / 10;
        if (l1) {
            l1 = l1->next;
        }
        if (l2) {
            l2 = l2->next;
        }
    }
    if (carry > 0) {
        tail->next = malloc(sizeof(struct ListNode));
        tail->next->val = carry;
        tail->next->next = NULL;
    }
    return head;
}
```
```

struct ListNode* addTwoNumbers(struct ListNode* l1, struct ListNode* l2){
    struct ListNode *tail=NULL,*head=NULL;
    
    
    int carry=0;
    while(l1!=NULL&&l2!=NULL){
        if(head==NULL){
            head=tail=malloc(sizeof(struct ListNode));
        }else{
            tail->next=malloc(sizeof(struct ListNode));
            tail=tail->next;    
        }
        tail->next=NULL;
        tail->val=(l1->val+l2->val+carry)%10;
        carry=(l1->val+l2->val+carry)/10;
        l1=l1->next;
        l2=l2->next;
    }
    if(l1==NULL){
        while(l2!=NULL){
            tail->next = malloc(sizeof(struct ListNode));
            tail = tail->next;
            tail->next=NULL;
            tail->val=(l2->val+carry)%10;
            carry=(l2->val+carry)/10;
            l2=l2->next;
        }
    }
    if(l2==NULL){
        while(l1!=NULL){
            tail->next = (struct ListNode*)malloc(sizeof(struct ListNode));
            tail = tail->next;
            tail->next=NULL;
            tail->val=(l1->val+carry)%10;
            carry=(l1->val+carry)/10;
            l1=l1->next;
        }
    }
    if(carry!=0){
        tail->next=malloc(sizeof(struct ListNode));
        tail=tail->next;
        tail->val=carry;
        tail->next=NULL;
    }
    return head;
}
```