## Lists 
A ***list*** is a common ADT for holding ordered data, having operations like append a data item, remove a data item, check if a data item exists, and print the list.

### Common List Operations:
| Operation         | Description                                       | Example                                                              |
|------------------|---------------------------------------------------|----------------------------------------------------------------------|
| Append(X)         | Inserts X at end of list                          | `list.Append(44)` → list: (99, 77, 44)                               |
| Prepend(X)        | Inserts X at start of list                        | `list.Prepend(44)` → list: (44, 99, 77)                              |
| InsertAfter(W, X) | Inserts X after W                                 | `list.InsertAfter(99, 44)` → list: (99, 44, 77)                      |
| Remove(X)         | Removes X                                         | `list.Remove(77)` → list: (99)                                       |
| Contains(X)       | Returns true if X is in the list, false otherwise| `list.Contains(99)` → true<br>`list.Contains(22)` → false            |
| Print()           | Prints list's items in order                      | `list.Print()` → outputs: 99, 77                                     |
| Sort()            | Sorts list's items in ascending order            | `list.Sort()` → list: (77, 99)                                       |
| IsEmpty()         | Returns true if list has no items                 | `list.IsEmpty()` → false                                             |
| GetLength()       | Returns the number of items in the list          | `list.GetLength()` → 2                                               |\

## Singly-Linked Lists
A ***singly-linked list*** is a data structure for implementing a list ADT, where each node has data and a pointer to the next node\
The singly-linked list append operation inserts a new node after the list's tail node. The append algorithm behavior differs if the list is empty versus not empty:
- **Append to empty list**: If the list's head is `null`, the list's `head` and `tail` are assigned with the new node.
- **Append to non-empty list**: If the list's head is not `null`, the `tail` node's `next` is first assigned with the new node, then the list's `tail` is assigned with the new node.

Given a new node, the prepend operation for a singly-linked list inserts the new node before the list's head node. The prepend algorithm behavior differs if the list is empty versus not empty:
- **Prepend to empty list**: If the list's head pointer is `null`, the list's `head` and `tail` pointers are assigned with the new node.
- **Prepend to non-empty list**: If the list's head pointer is not `null`, the new node's `next` pointer is first assigned with the list's `head` node, then the list's `head` pointer is assigned with the new node.

**Linked list search**: Given a data value, the search algorithm returns the first node whose data matches the value, or `null` if no match is found.
- The algorithm starts at the list's `head` and:
  - Checks if the current node's data matches the value.
  - If not, moves to the `next` node and repeats.
- If the current node becomes `null`, the algorithm returns `null` (no match found).

Given a new node, the insert-node-after operation for a singly-linked list inserts the new node after a provided existing list node.\
CurrentNode is a pointer to an existing list node but can be null when inserting into an empty list. The insert-node-after algorithm considers three insertion scenarios:
- **Insert as first node**: If the list's `head` is `null`, set both `head` and `tail` to the new node.
- **Insert after tail node**: If the list is not empty and `currentNode` is the `tail`, set `tail.next` and `tail` to the new node.
- **Insert in middle of list**: If the list is not empty and `currentNode` is not the `tail`, set the new node's `next` to `currentNode.next`, then set `currentNode.next` to the new node.

The `InsertAfter(int currentItem, int newItem)` function is used to insert a new item after a specified item in a singly-linked list implementation of a List ADT. Since the operation uses item values (not node references), it works as follows:

1. **Search for Node**: Calls `Search()` to locate the node containing `currentItem`.
2. **Allocate New Node**: If the node is found, a new node is created for `newItem`.
3. **Insert Node**: Calls `InsertNodeAfter()` to insert the new node immediately after the located node.

This approach maintains abstraction by working with data values rather than internal node pointers.

Remove-node-after operation removes the node after the specified list node. The existing node must be specified because each node in a singly-linked list only maintains a pointer to the next node.\
The `Remove(int item)` function is used to delete an item from a singly-linked list in a List ADT. Since it takes a data item as a parameter (not a node reference), the function works as follows:

1. **Search for Node**: Traverses the list to find the node containing the specified `item`, while keeping track of the previous node.
2. **Call RemoveNodeAfter()**: Once the node to remove is found, `RemoveNodeAfter()` is called with the previous node as the argument.

This method ensures that the correct node is removed while maintaining the abstraction of working with item values instead of node pointers.

## Doubly-Linked List
- A **doubly-linked list** is a data structure used to implement a list ADT.
- Each node contains:
  - **Data**
  - A pointer to the **next** node
  - A pointer to the **previous** node
- The list structure maintains pointers to:
  - The **head** (first node)
  - The **tail** (last node)

#### Key Characteristics:
- Unlike a singly-linked list, each node in a doubly-linked list has two pointers.
- It is called **"doubly-linked"** because of these two links (next and previous).
- It is a type of **positional list**, where elements are aware of their neighbors through these pointers.

The `append` operation inserts a new node **after the tail node** of the list. The behavior varies based on whether the list is empty or not:

- **Append to an Empty List**:
  - If `head` is `null`, set both `head` and `tail` to the new node.

- **Append to a Non-Empty List**:
  - Set `tail.next` to the new node.
  - Set `newNode.prev` to the current `tail`.
  - Update the `tail` pointer to point to the new node.

The `prepend` operation inserts a new node **before the head node** of the list and updates the head pointer to the new node. Behavior differs based on whether the list is empty:

- **Prepend to an Empty List**:
  - If `head` is `null`, set both `head` and `tail` to the new node.

- **Prepend to a Non-Empty List**:
  - Set `newNode.next` to the current `head`.
  - Set `head.prev` to the new node.
  - Update the `head` pointer to point to the new node.

The `search` operation finds the **first node** with data matching a given value. It works as follows:

- Start at the **head** node.
- While the current node is not `null`:
  - If `current.data == value`, return the current node.
  - Otherwise, move to `current.next`.
- If no match is found (i.e. current becomes `null`), return `null`.

The `insertNodeAfter(existingNode, newNode)` operation inserts `newNode` **after** a specified `existingNode`. It handles three scenarios:

- **Insert into an Empty List**:
  - Set both `head` and `tail` to the `newNode`.

- **Insert After Tail Node**:
  - Set `tail.next` to `newNode`.
  - Set `newNode.prev` to `tail`.
  - Update `tail` to point to `newNode`.

- **Insert Between Two Nodes**:
  - Set `newNode.next` to `existingNode.next`.
  - Set `newNode.prev` to `existingNode`.
  - Set `existingNode.next.prev` to `newNode`.
  - Set `existingNode.next` to `newNode`.

The `InsertAfter(int currentItem, int newItem)` function inserts `newItem` after `currentItem` in the list. Since the List ADT uses item values, not node references, the function works as follows:

- Call `Search()` to find the node containing `currentItem`.
- If found:
  - Create a new node for `newItem`.
  - Call `InsertNodeAfter()` to insert the new node after the found node.


The `removeNode(currentNode)` operation removes a specific node from a doubly-linked list. It handles the update of pointers based on four conditions:

- **Successor Exists**:  
  If `currentNode.next` is not `null`, set `currentNode.next.prev` to `currentNode.prev`.

- **Predecessor Exists**:  
  If `currentNode.prev` is not `null`, set `currentNode.prev.next` to `currentNode.next`.

- **Removing Head Node**:  
  If `currentNode` is the head, update the list’s `head` to `currentNode.next`.

- **Removing Tail Node**:  
  If `currentNode` is the tail, update the list’s `tail` to `currentNode.prev`.

The `Remove(int item)` function removes a node containing the specified item. Since the List ADT works with item values (not nodes), the process is:

- Call `Search()` to find the node containing `item`.
- If the node is found (not `null`), pass it to `RemoveNode()` to remove it from the list.

A **list traversal** algorithm visits each node in the list exactly once and performs an operation (e.g., printing the node’s data).

#### Steps:
- Start with a pointer set to the **head** of the list.
- While the pointer is not `null`:
  - Perform the desired operation (e.g., print node data).
  - Move the pointer to the **next** node.
- Traversal ends when the pointer becomes `null`.

Works for both **singly-linked** and **doubly-linked** lists.

A doubly-linked list also supports a reverse traversal. A reverse traversal visits all nodes starting with the list's tail node and ending after visiting the list's head node.

### Array-Based List (List ADT)

An **array-based list** implements the List ADT using an underlying array. It supports common operations like:
- `append`
- `prepend`
- `insert-after`
- `remove`
- `search`

#### Key Concepts:
- Arrays in C++ have **fixed sizes**.
- The list starts with a small allocated array (e.g., size 1–4).
- A `length` variable tracks how many elements are currently in use.
- When `length == capacity`, the array is **reallocated to a larger size** before adding new items.

#### Append Operation:
- Given a new element and list of length `X`, the element is inserted at **index `X`** (the end of the list).

When an item is added and the list's **length equals the allocation size**, the array must be resized:

- A **new, larger array** is allocated (commonly double the current size).
- All existing elements are **copied** to the new array.
- The new array becomes the list's storage array.

#### Performance:
- The resize operation has a **runtime complexity of O(n)**,  
  where `n` is the number of elements in the list (due to copying).
