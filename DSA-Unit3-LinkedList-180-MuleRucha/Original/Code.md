# College Lost & Found System

```cpp
#include <iostream>
#include <string>
using namespace std;

struct Node
{
    int id;
    string name;
    string status;
    Node *next;
};

Node *head = NULL;

// Add Item
void addItem()
{
    Node *newNode = new Node;

    cout << "Enter Item ID: ";
    cin >> newNode->id;

    cout << "Enter Item Name: ";
    cin >> newNode->name;

    cout << "Enter Status (Lost/Found): ";
    cin >> newNode->status;

    newNode->next = head;
    head = newNode;

    cout << "Item Added Successfully!\n";
}

// Display Items
void display()
{
    Node *temp = head;

    if (head == NULL)
    {
        cout << "No Items Available!\n";
        return;
    }

    while (temp != NULL)
    {
        cout << "\nID: " << temp->id;
        cout << "\nName: " << temp->name;
        cout << "\nStatus: " << temp->status << endl;

        temp = temp->next;
    }
}

// Search Item
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
            cout << "Item Found!\n";
            cout << "Name: " << temp->name << endl;
            cout << "Status: " << temp->status << endl;
            return;
        }

        temp = temp->next;
    }

    cout << "Item Not Found!\n";
}

// Delete Item
void deleteItem()
{
    int id;
    cout << "Enter Item ID to delete: ";
    cin >> id;

    Node *temp = head;
    Node *prev = NULL;

    while (temp != NULL)
    {
        if (temp->id == id)
        {
            if (prev == NULL)
                head = temp->next;
            else
                prev->next = temp->next;

            delete temp;
            cout << "Item Deleted Successfully!\n";
            return;
        }

        prev = temp;
        temp = temp->next;
    }

    cout << "Item Not Found!\n";
}

int main()
{
    int choice;

    do
    {
        cout << "\n--- College Lost & Found ---";
        cout << "\n1. Add Item";
        cout << "\n2. Search Item";
        cout << "\n3. Delete Item";
        cout << "\n4. Display Items";
        cout << "\n5. Exit";

        cout << "\nEnter Choice: ";
        cin >> choice;

        switch (choice)
        {
        case 1:
            addItem();
            break;

        case 2:
            searchItem();
            break;

        case 3:
            deleteItem();
            break;

        case 4:
            display();
            break;

        case 5:
            cout << "Thank You!";
            break;

        default:
            cout << "Invalid Choice!";
        }

    } while (choice != 5);

    return 0;
}
```

