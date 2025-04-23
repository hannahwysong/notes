## Queue - Abstract Data Type (ADT)

A **queue** is an Abstract Data Type (ADT) representing a collection where:
- Items are **inserted at the end**
- Items are **removed from the front**

### Key Operations
- **Enqueue**: Inserts an item at the end of the queue.
- **Dequeue**: Removes and returns the item from the front of the queue.

### Characteristics
- **FIFO (First-In, First-Out)**: The first item added is the first one removed.

### Implementation
A queue can be implemented using:
- Linked List
- Array

### Real-World Analogy
A queue works like **waiting in line at a grocery store**:
- New people join at the end of the line.
- The person at the front is served first and exits the line.

### Table 4.4.1: Common Queue ADT Operations

| Operation     | Description                                      | Example (Starting Queue: 43, 12, 77 — front is 43)             |
|---------------|--------------------------------------------------|----------------------------------------------------------------|
| `Enqueue(x)`  | Inserts `x` at the end of the queue              | `queue.Enqueue(56)` → Queue: 43, 12, 77, 56                    |
| `Dequeue()`   | Returns and removes the item at the front        | `queue.Dequeue()` → Returns: 43 → Queue: 12, 77                |
| `Peek()`      | Returns but does not remove the front item       | `queue.Peek()` → Returns: 43 → Queue still: 43, 12, 77         |
| `IsEmpty()`   | Returns `true` if the queue has no items         | `queue.IsEmpty()` → Returns: false → Queue still: 43, 12, 77   |
| `GetLength()` | Returns the number of items in the queue         | `queue.GetLength()` → Returns: 3 → Queue still: 43, 12, 77     |

Note: Dequeue() and Peek() operations should not be applied to an empty queue; the resulting behavior may be undefined.

### Queue Implementation Using a Linked List

A queue is often implemented using a **singly-linked list**, where:
- The **head node** represents the **front** of the queue.
- The **tail node** represents the **end** of the queue.

### Queue Operations with a Linked List

#### Enqueue Operation
- Create a new linked list node.
- Assign the node’s data with the item to enqueue.
- Append the node to the **tail** of the list.
- If the queue is empty, set both `head` and `tail` to the new node.

#### Dequeue Operation
- Assign a local variable with the data from the **head** node.
- Remove the head node from the list (advance `head` to the next node).
- If the queue becomes empty, set `tail` to `nullptr`.
- Return the local variable.

