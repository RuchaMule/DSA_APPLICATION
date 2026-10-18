## Algorithm

**Step 1:** Start the program.

**Step 2:** Define a structure `Node` containing Item ID, Item Name, Status (Lost/Found), and a pointer named `next`.

**Step 3:** Initialize `head = NULL`.

**Step 4:** Display a menu with options to add, search, remove, display items, and exit.

**Step 5:** To add an item, create a new node dynamically and accept its ID, name, and status from the user.

**Step 6:** If the linked list is empty, make the new node the head; otherwise, traverse the list and add the new node at the end.

**Step 7:** To search for an item, traverse the list using Item ID and display the details if the item is found.

**Step 8:** To remove an item, find its node, adjust the links, and delete the node from memory.

**Step 9:** To display items, start from `head`, traverse the list, and display each item's details.

**Step 10:** Repeat the menu until the user selects Exit.

**Step 11:** Stop the program.
