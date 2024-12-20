# kiran
c project

// implimentation of stack by linkedlist
#include <stdio.h>
#include <stdlib.h>

struct Node {
    int data;
    struct Node* next;
};

struct Node* head = NULL;

void push(int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->next = head;
    head = newNode;
}

void pop() {
    if (head == NULL) {
        printf("Stack is empty\n");
        return;
    }
    struct Node* temp = head;
    head = head->next;
    free(temp);
}

void display() {
    struct Node* p = head;
    while (p != NULL) {
        printf("%d ", p->data);
        p = p->next;
    }
    printf("\n");
}

int main() {
    push(4);
    push(9);
    push(8);

    pop();
    pop();
    pop();
    pop();

    display();

    return 0;
}
// implimentation of stack by array

struct Stack
{
    int size;
    int top;
    int *S;

};

void create(struct Stack *st)
{
    printf("enter size of an array");
    scanf("%d", & st->size);
    st->top=-1;
    st->S=(int *)malloc(st->size*sizeof(int));

}

void Display(struct Stack st)
{
    int i;
    for(i=st.top;i>=0;i--)
        printf("%d", st.S[i]);
    printf("\n");

}

void push(struct Stack *st, int x)
{
    if(st->top==st->size-1)
        printf("stack overflow\n");
    else
    {
        st->top++;
        st->S[st->top]=x;
    }

}

int pop(struct Stack *st)
{
    int x=-1;
    if (st->top==-1)
        printf("stack is underflow\n");
    else
    {
        x=st->S[st->top--];

    }
    return x;

}

int peek(struct Stack st, int index)
{
    int x=-1;
    if(st.top-index+1<0)
        printf("invalid index\n");
    x=st.S[st.top-index+1];

    return x;

}

int isEmpty(struct Stack st)
{
    if (st.top==-1)
         return 1;
    return 0;
}

int isfull(struct Stack st)
{
    return st.top==st.size-1;
}

int stacktop(struct Stack st)
{
    if(!isEmpty(st))
       return st.S[st.top];
    return -1;

}

int main()
{
    struct Stack st;
    create(&st);

    push(&st,400);
    push(&st,460);
    push(&st,520);
    push(&st,782);
    push(&st,473);
    push(&st,403);

    //pop(&st);
    //pop(&st);

    peek(st,4);

    Display(st);

    return 0;

}

