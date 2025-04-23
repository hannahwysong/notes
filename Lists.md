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
  -Append to empty list: If the list's head is null, the list's head and tail are assigned with the new node.
  -Append to non-empty list: If the list's head is not null, the tail node's next is first assigned with the new node, then the list's tail is assigned with the new node.


