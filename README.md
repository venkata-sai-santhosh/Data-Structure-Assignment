# Data-Structure-Assignment

## Q1: Reverse a String using Stack

### Algorithm
1. Start  
2. Read the string  
3. Push each character into stack  
4. Pop characters one by one  
5. Print popped characters (reversed string)  
6. Stop  

### Code
```c
#include <stdio.h>
#include <string.h>

#define MAX 100

char stack[MAX];
int top = -1;

void push(char ch) {
    stack[++top] = ch;
}

char pop() {
    return stack[top--];
}

int main() {
    char str[100];
    int i;

    printf("Enter string: ");
    scanf("%s", str);

    for(i = 0; i < strlen(str); i++) {
        push(str[i]);
    }

    printf("Reversed string: ");
    while(top != -1) {
        printf("%c", pop());
    }

    return 0;
}
```

---

## Q2: Balanced Parentheses

### Algorithm
1. Start  
2. Read expression  
3. Push '(' into stack  
4. If ')' found → pop  
5. If stack empty → balanced  
6. Else → not balanced  
7. Stop  

### Code
```c
#include <stdio.h>
#include <string.h>

char stack[100];
int top = -1;

void push(char ch) {
    stack[++top] = ch;
}

void pop() {
    if(top != -1) top--;
}

int main() {
    char exp[100];
    int i;

    printf("Enter expression: ");
    scanf("%s", exp);

    for(i = 0; i < strlen(exp); i++) {
        if(exp[i] == '(')
            push('(');
        else if(exp[i] == ')') {
            if(top == -1) {
                printf("Not Balanced");
                return 0;
            }
            pop();
        }
    }

    if(top == -1)
        printf("Balanced Expression");
    else
        printf("Not Balanced");

    return 0;
}
```

---

## Q3: Next Greater Element

### Algorithm
1. Start  
2. Read array  
3. Traverse array  
4. Compare each element with next  
5. Find next greater element  
6. If none → print -1  
7. Stop  

### Code
```c
#include <stdio.h>

int main() {
    int arr[] = {4, 5, 2, 10, 8};
    int n = 5;
    int i, j, next;

    for(i = 0; i < n; i++) {
        next = -1;
        for(j = i + 1; j < n; j++) {
            if(arr[j] > arr[i]) {
                next = arr[j];
                break;
            }
        }
        printf("%d -> %d\n", arr[i], next);
    }

    return 0;
}
```

---

## Q4: Printer Queue Simulation

### Algorithm
1. Start  
2. Create queue  
3. Show menu  
4. Insert document (enqueue)  
5. Print document (dequeue)  
6. Display queue  
7. Stop  

### Code
```c
#include <stdio.h>

#define MAX 5

int queue[MAX], front = -1, rear = -1;

void enqueue(int x) {
    if(rear == MAX - 1)
        printf("Queue Full\n");
    else {
        if(front == -1)
            front = 0;
        queue[++rear] = x;
    }
}

void dequeue() {
    if(front == -1)
        printf("Queue Empty\n");
    else {
        printf("Printed document: %d\n", queue[front]);
        front++;
        if(front > rear)
            front = rear = -1;
    }
}

void display() {
    int i;
    if(front == -1)
        printf("No documents\n");
    else {
        for(i = front; i <= rear; i++)
            printf("%d ", queue[i]);
    }
    printf("\n");
}

int main() {
    int ch, x;

    while(1) {
        printf("\n1.Add\n2.Print\n3.Display\n4.Exit\n");
        scanf("%d", &ch);

        switch(ch) {
            case 1:
                printf("Enter document id: ");
                scanf("%d", &x);
                enqueue(x);
                break;

            case 2:
                dequeue();
                break;

            case 3:
                display();
                break;

            case 4:
                return 0;
        }
    }
}
```

---

## Q5: Circular Queue

### Algorithm
1. Start  
2. Initialize queue  
3. Enqueue using circular logic  
4. Dequeue using circular logic  
5. Display elements  
6. Stop  

### Code
```c
#include <stdio.h>

#define MAX 5

int queue[MAX], front = -1, rear = -1;

void enqueue(int x) {
    if((rear + 1) % MAX == front)
        printf("Queue Full\n");
    else {
        if(front == -1)
            front = 0;
        rear = (rear + 1) % MAX;
        queue[rear] = x;
    }
}

void dequeue() {
    if(front == -1)
        printf("Queue Empty\n");
    else {
        printf("Deleted: %d\n", queue[front]);
        if(front == rear)
            front = rear = -1;
        else
            front = (front + 1) % MAX;
    }
}

void display() {
    int i;

    if(front == -1)
        printf("Queue Empty\n");
    else {
        i = front;
        while(1) {
            printf("%d ", queue[i]);
            if(i == rear)
                break;
            i = (i + 1) % MAX;
        }
    }
    printf("\n");
}

int main() {
    int ch, x;

    while(1) {
        printf("\n1.Enqueue\n2.Dequeue\n3.Display\n4.Exit\n");
        scanf("%d", &ch);

        switch(ch) {
            case 1:
                printf("Enter value: ");
                scanf("%d", &x);
                enqueue(x);
                break;

            case 2:
                dequeue();
                break;

            case 3:
                display();
                break;

            case 4:
                return 0;
        }
    }
}
```

---
