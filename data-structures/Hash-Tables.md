## Summary: Hash Tables and Hash Maps

A **hash table** is a data structure that stores unordered items by hashing each item to a location in an array. Each element in the array is called a **bucket**.

A **hash map** implements a Map ADT using a hash table. It supports operations like `insert`, `get`, and `remove`, each of which uses a key. The key is mapped to a bucket using the following steps:

1. **Compute the hash code:**
   ```
   hashCode = Call hash function for key
   ```

2. **Map the hash code to a valid bucket index:**
   ```
   bucketIndex = hashCode % arrayAllocationSize
   ```
This step addresses the issue that an array can't be large enough to support all possible integer values.\
By using the modulus operator, the `bucketIndex` is guaranteed to be within the bounds of the array.

## Summary: Hash Table Collisions

A **collision** occurs in a hash table when two different keys map to the same bucket index.

**Example:**  
In a table with 10 buckets, inserting key `16` might cause a collision if it hashes to bucket `6`, which is already occupied by key `86`.

### Collision Resolution Techniques

- **Chaining:**  
  Each bucket holds a list of items. Multiple keys that hash to the same bucket are stored in this list.  
  *Example:* Bucket 6 could contain `[86, 16]`.

- **Open Addressing:**  
  When a collision occurs, the table searches for the next available bucket to store the item.  
  *Example:* If bucket 6 is full, key `16` might be stored in bucket 7.

These techniques are covered in more detail in other sections.

## Summary: Chaining in Hash Tables

**Chaining** is a technique for handling hash table collisions by associating each bucket with a list (typically a linked list). Multiple items that hash to the same bucket are stored in that list.

### Operations Using Chaining

Each operation starts by hashing the key to find the appropriate bucket, then searches that bucket's list:

- **Get:**  
  Return the value associated with the key, or `null` if the key is not found.

- **Insert:**  
  - If the key is found in the list, update its value.
  - If the key is not found, append a new node with the key and value to the list.

- **Remove:**  
  If the key is found, remove the corresponding node from the list.

## Summary: Chaining Hash Table Classes

### `ChainingHashTableItem` Class

Represents an individual item in a hash table that uses **chaining** for collision resolution.

**Attributes:**
- `key`: The item's key.
- `value`: The associated value.
- `next`: A pointer to the next item in the chain (linked list).

### `ChainingHashTable` Class

Implements the hash table using an **array or vector of `ChainingHashTableItem` pointers**.

**Components:**
- **Member Variable:**  
  - Typically an array or vector that holds the head pointers of each bucket’s linked list.
  
- **Constructor:**  
  - Initializes the data structure, likely including allocating space for the array/vector.

- **Destructor:**  
  - Cleans up memory by deallocating all nodes in the chains and the array/vector itself.

*Note: The class declaration shown is partial, containing only the member variable, constructor, and destructor declarations.*

## Summary: Hash Function in `ChainingHashTable`

### `Hash()` Function

The `ChainingHashTable` class uses the `Hash()` function to compute bucket indices for keys.

- Utilizes `std::hash<K>` to generate an **unsigned integer hash code** for the key.
- The **high bit of the hash code is set to 0**, ensuring the result fits within the range of an `int`.
- Returns a valid **non-negative integer** hash code.

### Usage in Member Functions

The `Hash()` function is used by the following operations to determine the appropriate bucket:

- **Insert()**
- **Get()**
- **Remove()**

These functions rely on `Hash()` to compute the index into the hash table's array or vector of buckets.

A hash table with linear probing handles a collision by starting at the key's mapped bucket, and then linearly searches subsequent buckets until an empty bucket is found. 

## Summary: Linear Probing and Empty Bucket Types

### Types of Empty Buckets

Linear probing distinguishes between two types of empty buckets:

- **Empty-since-start:**  
  The bucket has never held an item since the hash table was created.

- **Empty-after-removal:**  
  The bucket previously held an item, but that item was removed.

This distinction is **critical during searches**.

### Search Algorithm (Linear Probing)

1. Use the key to compute the initial bucket index.
2. Probe buckets linearly (one by one):
   - Stop if a **matching key** is found.
   - Stop if an **empty-since-start** bucket is found (item doesn't exist).
   - Continue past **empty-after-removal** buckets.
   - Stop if **all buckets** have been checked (item doesn't exist).

### Remove Algorithm

1. Search for the key using the search procedure.
2. If the key is found:
   - Remove the item.
   - Mark the bucket as **empty-after-removal**.

## Summary: Linear Probing with Open Addressing

### Open Addressing Bucket States

In a hash table using **open addressing**, each bucket can be in one of three states:

1. **Occupied:**  
   Holds a key and value.

2. **Empty Since Start:**  
   Has never held an item.

3. **Empty After Removal:**  
   Previously held an item, but it has been removed.

### `OpenAddressingBucket` Class

- Contains member variables for a **key** and **value**.
- Includes two static instances:
  - `EMPTY_SINCE_START`
  - `EMPTY_AFTER_REMOVAL`

These instances are used to mark the state of each bucket.

### `LinearProbingHashTable` Class

- Contains a **vector of `OpenAddressingBucket*` pointers**, one for each bucket.
- On initialization, each bucket pointer is set to point to the `EMPTY_SINCE_START` static instance.

This setup helps in efficiently managing and checking the state of each bucket during operations like insert, get, and remove.

## Summary: Insert Algorithm (Linear Probing)

### Insertion Steps

1. **Search for the Key:**
   - If the key already exists in the table, update its associated value.

2. **If Key is Not Found:**
   - Restart the probing sequence from the original hash index.
   - Insert the key-value pair into the **first empty bucket** found (either `EMPTY_SINCE_START` or `EMPTY_AFTER_REMOVAL`).

### Return Value

- Returns `true` if the item was successfully inserted.
- Returns `false` if **all buckets are occupied** and no empty spot is found.

The search algorithm uses the probing sequence until the key being searched for is found or an empty-since-start bucket is found.\
The removal algorithm searches for the key to remove and, if found, marks the bucket as empty-after-removal.

## Participation Activity 5.5.6: Choosing Good `c1` and `c2` for Quadratic Probing

When implementing quadratic probing in a hash table:

- Some choices for `c1` and `c2` can cause problems.
  - Example: Choosing `c1 = 10` and `c2 = 10` for a table with 10 buckets will cause the probe to repeatedly compute the same index.
- Important guideline: `c1` and `c2` should **not** be multiples of the number of buckets.

### Simplified Formula
Some implementations choose `c1 = 0` and `c2 = 1`, which simplifies the probing sequence formula to: index = (H + i^2) mod tablesize

where:
- `H` is the original hash value
- `i` is the probe attempt number (0, 1, 2, ...)

## 5.6 Pseudo-random Probing (Study Notes)

- **Goal**: Avoid primary clustering by randomizing the probing order.

- **Setup**:
  - Create an `offsets` array of size `N - 1`.
  - Fill with numbers `1` to `N-1`.
  - Shuffle randomly.

- **Probing formula**:
  ```
  probe = (home + offsets[i]) % N
  ```
  where `home = hash(k) = k % N`.

- **Example (N = 10)**:
  ```
  offsets = [4, 7, 2, 9, 1, 8, 6, 3, 5]
  k = 1088
  home = 1088 % 10 = 8
  ```

- **Probing sequence**:
  ```
  probe_0 = (8 + 4) % 10 = 2
  probe_1 = (8 + 7) % 10 = 5
  probe_2 = (8 + 2) % 10 = 0
  probe_3 = (8 + 9) % 10 = 7
  probe_4 = (8 + 1) % 10 = 9
  ...

- **Important**:
  - All buckets are eventually probed.
  - If `offsets` were not shuffled, probing would behave like **linear probing**.
