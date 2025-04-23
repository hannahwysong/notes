## Deque - Double-Ended Queue (ADT)

A **deque** (pronounced *"deck"*, short for **double-ended queue**) is an Abstract Data Type (ADT) in which items can be **inserted and removed at both the front and the back**.

### Key Operations

- **Push-front**: Inserts an item at the **front** of the deque.
- **Push-back**: Inserts an item at the **back** of the deque.
- **Pop-front**: Removes and returns the item from the **front** of the deque.
- **Pop-back**: Removes and returns the item from the **back** of the deque.

### Implementation

A deque can be implemented using:
- A **linked list**
- An **array**

> Deques combine the features of both stacks and queues, offering maximum flexibility for insertion and removal.

### Table 4.7.1: Common Deque ADT Operations

| Operation       | Description                                             | Example (Starting Deque: 59, 63, 19 — front is 59)                 |
|-----------------|---------------------------------------------------------|----------------------------------------------------------------------|
| `PushFront(x)`  | Inserts `x` at the front of the deque                   | `deque.PushFront(41)` → Deque: 41, 59, 63, 19                       |
| `PushBack(x)`   | Inserts `x` at the back of the deque                    | `deque.PushBack(41)` → Deque: 59, 63, 19, 41                        |
| `PopFront()`    | Returns and removes the item at the front              | `deque.PopFront()` → Returns: 59 → Deque: 63, 19                    |
| `PopBack()`     | Returns and removes the item at the back               | `deque.PopBack()` → Returns: 19 → Deque: 59, 63                     |
| `PeekFront()`   | Returns but does not remove the front item             | `deque.PeekFront()` → Returns: 59 → Deque still: 59, 63, 19         |
| `PeekBack()`    | Returns but does not remove the back item              | `deque.PeekBack()` → Returns: 19 → Deque still: 59, 63, 19          |
| `IsEmpty()`     | Returns `true` if deque is empty, `false` otherwise    | `deque.IsEmpty()` → Returns: false → Deque still: 59, 63, 19        |
| `GetLength()`   | Returns the number of items in the deque               | `deque.GetLength()` → Returns: 3 → Deque still: 59, 63, 19          |
