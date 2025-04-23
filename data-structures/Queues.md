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

### Queue Implementation Using an Array

A queue can also be implemented using an **array**, along with three additional variables:

- **`allocationSize`**: The total allocated size of the array.
- **`length`**: The number of items currently in the queue.
- **`frontIndex`**: The index of the front item in the array.

#### Queue Content
- The queue starts at `array[frontIndex]`.
- Items continue forward for `length` elements.
- If the end of the array is reached, the queue **wraps around** to the beginning of the array (circular buffer behavior).

### Bounded vs. Unbounded Queue

#### Bounded Queue
A **bounded queue** has a maximum allowed length.

- **`maxLength`**: An additional variable specifying the queue’s maximum size.
- `maxLength` is typically set during construction and remains fixed throughout the queue’s lifetime.
- When `length == maxLength`, the queue is considered **full** and cannot accept new items until space is freed.

#### Unbounded Queue
An ***unbounded queue*** has no fixed maximum size.

- It can grow dynamically as more items are added.
- Typically implemented using a linked list or dynamically resizing array/vector.

### Supporting Bounded and Unbounded Queues with an Array

An array-based queue can be designed to support both **bounded** and **unbounded** behavior using the `maxLength` variable:

#### Behavior Based on `maxLength`
- If `maxLength` is **negative**:  
  → The queue is **unbounded** (can grow indefinitely).
- If `maxLength` is **nonnegative**:  
  → The queue is **bounded** (cannot exceed `maxLength` items).

#### Resize Operation
When the array needs more space, a **resize** is performed:

- A new array is allocated with a size that is typically **double the current allocation**.
- For **bounded queues**, the new size is the **minimum of**:
  - `maxLength`
  - `2 × current allocationSize`
- All existing queue elements are copied to the new array.
- The **front index is reset to 0** to maintain proper order and simplify indexing.

> This strategy allows for efficient scaling while still respecting maximum constraints when needed.

### Enqueue and Dequeue Operations (Array-Based Queue)

#### Enqueue Operation

1. **Check for Full Queue**:
   - If `length == maxLength`, the queue is **full**.
   - No item is added, and the function returns `false`.

2. **Check for Resize**:
   - If `length == allocationSize`, perform a **resize** operation.

3. **Compute Enqueue Index**:
   - The item is placed at:  
     `(frontIndex + length) % allocationSize`

   - **Example**:  
     Enqueueing `42` into a queue with:  
     `frontIndex = 2`, `length = 3`, `allocationSize = 8`  
     → Computed index = `(2 + 3) % 8 = 5`  
     → `array[5] = 42`

4. **Update Length**:
   - Increment `length`.

5. **Return**:
   - Return `true` to indicate the item was successfully enqueued.

---

#### Dequeue Operation

1. **Copy Front Item**:
   - Store `array[frontIndex]` in a local variable.

2. **Update Queue State**:
   - Decrement `length`.
   - Increment `frontIndex`.  
     → If `frontIndex == allocationSize`, reset it to `0` (wrap around).

3. **Return Item**:
   - Return the copied item from step 1.
