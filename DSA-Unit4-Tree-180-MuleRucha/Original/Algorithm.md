Algorithm: Threaded BST Predecessor and Successor
Step 1: Start the program.
Step 2: Define a Node structure containing data, left and right pointers, and lthread and rthread flags.
Step 3: Initialize the root pointer to NULL.
Step 4: Accept the number of nodes and insert the given values into the Threaded Binary Search Tree while maintaining the threads.
Step 5: Display the inorder traversal by starting from the leftmost node and repeatedly finding its inorder successor.
Step 6: Accept the value of the node whose inorder predecessor and successor are to be found.
Step 7: Search for the specified node. If the node is not found, display a message and stop.
Step 8: If the left pointer is a thread, consider it as the inorder predecessor. Otherwise, find the rightmost node in the left subtree.
Step 9: If the right pointer is a thread, consider it as the inorder successor. Otherwise, find the leftmost node in the right subtree.
Step 10: Display the inorder predecessor and successor wherever they exist. If either does not exist, display an appropriate message.
Step 11: Stop the program.
