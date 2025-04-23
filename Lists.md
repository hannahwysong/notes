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
| GetLength()       | Returns the number of items in the list          | `list.GetLength()` → 2                                               |

A ***singly-linked list*** is a data structure for implementing a list ADT, where each node has data and a pointer to the next node\
The singly-linked list append operation inserts a new node after the list's tail node. The append algorithm behavior differs if the list is empty versus not empty:
- **Append to empty list**: If the list's head is `null`, the list's `head` and `tail` are assigned with the new node.
- **Append to non-empty list**: If the list's head is not `null`, the `tail` node's `next` is first assigned with the new node, then the list's `tail` is assigned with the new node.

Given a new node, the prepend operation for a singly-linked list inserts the new node before the list's head node. The prepend algorithm behavior differs if the list is empty versus not empty:
- **Prepend to empty list**: If the list's head pointer is `null`, the list's `head` and `tail` pointers are assigned with the new node.
- **Prepend to non-empty list**: If the list's head pointer is not `null`, the new node's `next` pointer is first assigned with the list's `head` node, then the list's `head` pointer is assigned with the new node.

- **Linked list search**: Given a data value, the search algorithm returns the first node whose data matches the value, or `null` if no match is found.
- The algorithm starts at the list's `head` and:
  - Checks if the current node's data matches the value.
  - If not, moves to the `next` node and repeats.
- If the current node becomes `null`, the algorithm returns `null` (no match found).

Given a new node, the insert-node-after operation for a singly-linked list inserts the new node after a provided existing list node.\
CurrentNode is a pointer to an existing list node but can be null when inserting into an empty list. The insert-node-after algorithm considers three insertion scenarios:
- **Insert as first node**: If the list's `head` is `null`, set both `head` and `tail` to the new node.
- **Insert after tail node**: If the list is not empty and `currentNode` is the `tail`, set `tail.next` and `tail` to the new node.
- **Insert in middle of list**: If the list is not empty and `currentNode` is not the `tail`, set the new node's `next` to `currentNode.next`, then set `currentNode.next` to the new node.
