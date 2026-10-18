## Algorithm

**Step 1:** Start the program.

**Step 2:** Define a `Node` structure containing Item ID, Item Name, Status, and a pointer named `next`.

**Step 3:** Initialize `head`, `top`, `front`, and `rear` pointers to `NULL`.

**Step 4:** Display a menu with options to add, search, remove, display items, perform Stack operations, perform Queue operations, and exit.

**Step 5:** To add an item, create a new node dynamically and accept its ID, name, and status.

**Step 6:** If the linked list is empty, make the new node the `head`; otherwise, traverse the list and add the node at the end.

**Step 7:** To search for an item, traverse the list using Item ID and display the details if the item is found.

**Step 8:** To remove an item, find its node, adjust the links, and release the node's memory.

**Step 9:** For Stack Push, insert a node at `top`; for Stack Pop, remove the top node if the stack is not empty.

**Step 10:** For Queue Enqueue, insert a node at `rear`; for Queue Dequeue, remove a node from `front` if the queue is not empty.

**Step 11:** Use `calloc()` for dynamic memory allocation as required, ensuring that allocation and deallocation are compatible with the actual node structure.

**Step 12:** Repeat the menu until the user selects Exit.

**Step 13:** Stop the program.
