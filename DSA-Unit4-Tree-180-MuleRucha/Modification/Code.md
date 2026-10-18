# Threaded Binary Search Tree (TBST)

```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node *left, *right;
    bool lthread, rthread;
};

Node* createNode(int x) {
    Node* p = new Node;
    p->data = x;
    p->left = NULL;
    p->right = NULL;
    p->lthread = true;
    p->rthread = true;
    return p;
}

Node* insert(Node* root, int x) {
    Node* p = root;
    Node* parent = NULL;

    while (p != NULL) {
        if (x == p->data)
            return root;

        parent = p;

        if (x < p->data) {
            if (p->lthread == false)
                p = p->left;
            else
                break;
        } else {
            if (p->rthread == false)
                p = p->right;
            else
                break;
        }
    }

    Node* temp = createNode(x);

    if (parent == NULL) {
        root = temp;
    } else if (x < parent->data) {
        temp->left = parent->left;
        temp->right = parent;
        parent->left = temp;
        parent->lthread = false;
    } else {
        temp->left = parent;
        temp->right = parent->right;
        parent->right = temp;
        parent->rthread = false;
    }

    return root;
}

Node* findPred(Node* p) {
    if (p->lthread)
        return p->left;

    p = p->left;

    while (p->rthread == false)
        p = p->right;

    return p;
}

Node* findSucc(Node* p) {
    if (p->rthread)
        return p->right;

    p = p->right;

    while (p->lthread == false)
        p = p->left;

    return p;
}

Node* search(Node* root, int x) {
    Node* p = root;

    while (p != NULL) {
        if (p->data == x)
            return p;

        if (x < p->data) {
            if (p->lthread)
                return NULL;
            p = p->left;
        } else {
            if (p->rthread)
                return NULL;
            p = p->right;
        }
    }

    return NULL;
}

void showInorder(Node* root, int a[], int &n) {
    Node* p = root;

    if (p == NULL)
        return;

    while (p->lthread == false)
        p = p->left;

    while (p != NULL) {
        a[n++] = p->data;

        if (p->rthread)
            p = p->right;
        else {
            p = p->right;

            while (p->lthread == false)
                p = p->left;
        }
    }
}

int main() {
    Node* root = NULL;
    int n, x;
    int a[100], count = 0;
    bool correct = true;

    cout << "Enter number of nodes: ";
    cin >> n;

    if (n <= 0 || n > 100) {
        cout << "Invalid number of nodes.";
        return 0;
    }

    cout << "Enter node values: ";

    for (int i = 0; i < n; i++) {
        cin >> x;
        root = insert(root, x);
    }

    showInorder(root, a, count);

    cout << "\nInorder Traversal: ";
    for (int i = 0; i < count; i++)
        cout << a[i] << " ";

    cout << "\n\nNode\tPredecessor\tSuccessor\n";

    for (int i = 0; i < count; i++) {
        Node* p = search(root, a[i]);
        Node* pre = findPred(p);
        Node* suc = findSucc(p);

        cout << a[i] << "\t";

        if (pre == NULL)
            cout << "Not Exists";
        else
            cout << pre->data;

        cout << "\t\t";

        if (suc == NULL)
            cout << "Not Exists";
        else
            cout << suc->data;

        cout << "\n";

        if (i == 0) {
            if (pre != NULL)
                correct = false;
        } else {
            if (pre == NULL || pre->data != a[i - 1])
                correct = false;
        }

        if (i == count - 1) {
            if (suc != NULL)
                correct = false;
        } else {
            if (suc == NULL || suc->data != a[i + 1])
                correct = false;
        }
    }

    cout << "\nVerification: ";

    if (correct)
        cout << "Results match with inorder traversal.";
    else
        cout << "Results do not match.";

    return 0;
}
```

