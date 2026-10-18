# College Lost & Found Management System

```cpp
#include <iostream>
#include <cstdlib>
using namespace std;

struct Node
{
    int id;
    char name[50];
    char status[20];
    Node *next;
};

Node *head = NULL;
Node *top = NULL;
Node *front = NULL;
Node *rear = NULL;

// Input Item Details
void inputItem(Node *n)
{
    cout << "Enter Item ID: ";
    cin >> n->id;

    cout << "Enter Item Name: ";
    cin >> ws;
    cin.getline(n->name, 50);

    cout << "Enter Status (Lost/Found): ";
    cin >> n->status;
}

// 1. Add Item to Linked List
void addItem()
{
    Node *n = new Node;
    inputItem(n);
    n->next = NULL;

    if (head == NULL)
        head = n;
    else
    {
        Node *temp = head;
        while (temp->next != NULL)
            temp = temp->next;

        temp->next = n;
    }

    cout << "Item Added Successfully!\n";
}

// 2. Search Item
void searchItem()
{
    int id;
    cout << "Enter Item ID: ";
    cin >> id;

    Node *temp = head;

    while (temp != NULL)
    {
        if (temp->id == id)
        {
            cout << "Name: " << temp->name
                 << "\nStatus: " << temp->status << endl;
            return;
        }
        temp = temp->next;
    }

    cout << "Item Not Found!\n";
}

// 3. Display Items
void displayItems()
{
    Node *temp = head;

    if (temp == NULL)
    {
        cout << "No Items Available!\n";
        return;
    }

    while (temp != NULL)
    {
        cout << "\nID: " << temp->id
             << "\nName: " << temp->name
             << "\nStatus: " << temp->status << endl;

        temp = temp->next;
    }
}

// 4. Remove Item
void removeItem()
{
    int id;
    cout << "Enter Item ID to Remove: ";
    cin >> id;

    Node *temp = head;
    Node *prev = NULL;

    while (temp != NULL && temp->id != id)
    {
        prev = temp;
        temp = temp->next;
    }

    if (temp == NULL)
    {
        cout << "Item Not Found!\n";
        return;
    }

    if (prev == NULL)
        head = temp->next;
    else
        prev->next = temp->next;

    delete temp;
    cout << "Item Removed Successfully!\n";
}

// 5. Stack Push
void push()
{
    Node *n = new Node;
    inputItem(n);

    n->next = top;
    top = n;

    cout << "Item Pushed into Stack!\n";
}

// 6. Stack Pop
void pop()
{
    if (top == NULL)
    {
        cout << "Stack Underflow!\n";
        return;
    }

    Node *temp = top;
    cout << "Removed: " << temp->name << endl;

    top = top->next;
    delete temp;
}

// 7. Display Stack
void displayStack()
{
    Node *temp = top;

    if (temp == NULL)
    {
        cout << "Stack is Empty!\n";
        return;
    }

    while (temp != NULL)
    {
        cout << temp->id << " - " << temp->name << endl;
        temp = temp->next;
    }
}

// 8. Queue Enqueue
void enqueue()
{
    Node *n = new Node;
    inputItem(n);
    n->next = NULL;

    if (rear == NULL)
        front = rear = n;
    else
    {
        rear->next = n;
        rear = n;
    }

    cout << "Item Added to Queue!\n";
}

// 9. Queue Dequeue
void dequeue()
{
    if (front == NULL)
    {
        cout << "Queue Underflow!\n";
        return;
    }

    Node *temp = front;
    cout << "Processed: " << temp->name << endl;

    front = front->next;

    if (front == NULL)
        rear = NULL;

    delete temp;
}

// 10. Display Queue
void displayQueue()
{
    Node *temp = front;

    if (temp == NULL)
    {
        cout << "Queue is Empty!\n";
        return;
    }

    while (temp != NULL)
    {
        cout << temp->id << " - " << temp->name << endl;
        temp = temp->next;
    }
}

// 11. calloc() Demonstration
void callocDemo()
{
    int *arr = (int *)calloc(5, sizeof(int));

    if (arr == NULL)
    {
        cout << "Memory Allocation Failed!\n";
        return;
    }

    cout << "Array values: ";

    for (int i = 0; i < 5; i++)
        cout << arr[i] << " ";

    cout << "\nMemory allocated using calloc().\n";

    free(arr);
}

// Main Function
int main()
{
    int choice;

    do
    {
        cout << "\n--- College Lost & Found System ---\n";
        cout << "1. Add Item\n";
        cout << "2. Search Item\n";
        cout << "3. Display Items\n";
        cout << "4. Remove Item\n";
        cout << "5. Stack Push\n";
        cout << "6. Stack Pop\n";
        cout << "7. Display Stack\n";
        cout << "8. Queue Enqueue\n";
        cout << "9. Queue Dequeue\n";
        cout << "10. Display Queue\n";
        cout << "11. calloc Demonstration\n";
        cout << "0. Exit\n";
        cout << "Enter Choice: ";
        cin >> choice;

        switch (choice)
        {
            case 1: addItem(); break;
            case 2: searchItem(); break;
            case 3: displayItems(); break;
            case 4: removeItem(); break;
            case 5: push(); break;
            case 6: pop(); break;
            case 7: displayStack(); break;
            case 8: enqueue(); break;
            case 9: dequeue(); break;
            case 10: displayQueue(); break;
            case 11: callocDemo(); break;
            case 0: cout << "Thank You!\n"; break;
            default: cout << "Invalid Choice!\n";
        }

    } while (choice != 0);

    return 0;
}
```

