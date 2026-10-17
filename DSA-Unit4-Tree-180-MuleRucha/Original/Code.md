
```cpp
#include <iostream>
using namespace std;

struct Node
{
    int data;
    Node *left, *right;
    bool lthread, rthread;
};

Node* createNode(int data)
{
    Node* temp = new Node;
    temp->data = data;
    temp->left = NULL;
    temp->right = NULL;
    temp->lthread = true;
    temp->rthread = true;
    return temp;
}

Node* insert(Node* root, int key)
{
    Node* ptr = root;
    Node* parent = NULL;

    while (ptr != NULL)
    {
        if (key == ptr->data)
            return root;

        parent = ptr;

        if (key < ptr->data)
        {
            if (ptr->lthread == false)
                ptr = ptr->left;
            else
                break;
        }
        else
        {
            if (ptr->rthread == false)
                ptr = ptr->right;
            else
                break;
        }
    }

    Node* temp = createNode(key);

    if (parent == NULL)
        root = temp;
    else if (key < parent->data)
    {
        temp->left = parent->left;
        temp->right = parent;
        parent->lthread = false;
        parent->left = temp;
    }
    else
    {
        temp->right = parent->right;
        temp->left = parent;
        parent->rthread = false;
        parent->right = temp;
    }

    return root;
}

Node* search(Node* root, int key)
{
    Node* ptr = root;

    while (ptr != NULL)
    {
        if (ptr->data == key)
            return ptr;

        if (key < ptr->data)
        {
            if (ptr->lthread)
                return NULL;
            ptr = ptr->left;
        }
        else
        {
            if (ptr->rthread)
                return NULL;
            ptr = ptr->right;
        }
    }

    return NULL;
}

Node* predecessor(Node* ptr)
{
    if (ptr->lthread)
        return ptr->left;

    ptr = ptr->left;

    while (!ptr->rthread)
        ptr = ptr->right;

    return ptr;
}

Node* successor(Node* ptr)
{
    if (ptr->rthread)
        return ptr->right;

    ptr = ptr->right;

    while (!ptr->lthread)
        ptr = ptr->left;

    return ptr;
}

int main()
{
    Node* root = NULL;
    int n, value, key;

    cout << "Enter number of nodes: ";
    cin >> n;

    cout << "Enter node values: ";

    for (int i = 0; i < n; i++)
    {
        cin >> value;
        root = insert(root, value);
    }

    cout << "Enter specified node: ";
    cin >> key;

    Node* ptr = search(root, key);

    if (ptr == NULL)
    {
        cout << "Node not found in the tree.";
        return 0;
    }

    Node* pred = predecessor(ptr);
    Node* succ = successor(ptr);

    if (pred != NULL)
        cout << "Inorder Predecessor: "
             << pred->data << endl;
    else
        cout << "Inorder Predecessor does not exist."
             << endl;

    if (succ != NULL)
        cout << "Inorder Successor: "
             << succ->data << endl;
    else
        cout << "Inorder Successor does not exist."
             << endl;

    return 0;
}
```
