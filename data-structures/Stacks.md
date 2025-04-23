## Stack - Abstract Data Type (ADT)

A **stack** is an Abstract Data Type (ADT) that represents a collection where elements are added and removed **only from the top** of the stack.

### Key Operations
- **Push**: Inserts an item at the top of the stack.
- **Pop**: Removes and returns the item from the top of the stack.

### Characteristics
- **LIFO (Last-In, First-Out)**: The most recently added item is the first to be removed.

### Implementation
A stack can be implemented using:
- Linked List
- Array
- Vector

### Table 4.1.1: Common Stack ADT Operations

| Operation     | Description                                      | Example (Starting Stack: 99, 77 — top is 99)              |
|---------------|--------------------------------------------------|------------------------------------------------------------|
| `Push(x)`     | Inserts `x` on top of the stack                  | `stack.Push(44)` → Stack: 44, 99, 77                       |
| `Pop()`       | Removes and returns the top item of the stack    | `stack.Pop()` → Returns: 99 → Stack: 77                   |
| `Peek()`      | Returns but does not remove the top item         | `stack.Peek()` → Returns: 99 → Stack still: 99, 77        |
| `IsEmpty()`   | Returns `true` if the stack is empty             | `stack.IsEmpty()` → Returns: false → Stack still: 99, 77  |
| `GetLength()` | Returns the number of items in the stack         | `stack.GetLength()` → Returns: 2 → Stack still: 99, 77    |

### Linked-List Stacks
A stack is often implemented using a singly-linked list.\ 
The stack object has a pointer to the top node, and each node points to the node below.

- **Push Operation**
  - Create a new list node.
  - Assign the node's data with the item to be pushed.
  - Prepend the node to the beginning (top) of the linked list.

- **Pop Operation**
  - Assign a local variable with the data from the top node.
  - Remove the top node from the linked list.
  - Return the local variable.

### Array Stack

A stack can also be implemented using an array, along with two additional variables:

- **`allocationSize`**: An integer representing the total allocated size of the array.
- **`length`**: An integer representing the current number of items in the stack.

#### Characteristics:
- The **bottom item** is stored at `array[0]`.
- The **top item** is stored at `array[length - 1]`.
- If the stack is **empty**, `length` is `0`.

An unbounded stack is a stack with no upper limit on length.\ 
An unbounded stack's length can increase indefinitely, so the stack's array allocation size must also be able to increase indefinitely.

A bounded stack is a stack with a length that does not exceed a maximum value.\ 
The maximum is commonly the array's initial allocation size.\
Ex: A bounded stack with allocationSize = 100 cannot exceed a length of 100 items.

A bounded stack with a length equal to the maximum length is said to be full.

The ArrayStack class below can be used as an unbounded stack or a bounded stack.\
If the parameter passed to the constructor is negative, the stack is unbounded.\
If the parameter is nonnegative, the stack is bounded.
