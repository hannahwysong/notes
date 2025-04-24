## Map (Dictionary) - Abstract Data Type (ADT)

A **map** (also known as a **dictionary**) is an Abstract Data Type (ADT) that associates **keys** with **values**.

### Key Characteristics
- Each **key** is **unique** — duplicate keys are not allowed.
- A **value** is associated with each key.

### Key Operations

- **Insert (key, value)**:
  - If the key **does not exist**: the key-value pair is inserted.
  - If the key **already exists**: the value is **updated**.

- **Get (key)**:
  - Returns the value associated with the specified key.
  - Returns `null` (or `None` in Python) if the key **does not exist**.

### Table 5.1.1: Common Map ADT Operations

| Operation         | Description                                                                 | Example (Starting Map: `{ 5: "apple", 6: "banana", 10: "grapefruit" }`)                    |
|-------------------|-----------------------------------------------------------------------------|---------------------------------------------------------------------------------------------|
| `Insert(key, value)` | Inserts the key-value pair if the key does not exist; updates value if it does | `map.Insert(4, "pear")`<br>`map.Insert(6, "orange")`<br>Resulting Map:<br>`{ 5: "apple", 6: "orange", 10: "grapefruit", 4: "pear" }` |
| `Remove(key)`     | Removes the key and its associated value                                   | `map.Remove(10)`<br>Resulting Map:<br>`{ 5: "apple", 6: "banana" }`                        |
| `Get(key)`        | Returns the value for the key, or `null` if the key doesn't exist          | `map.Get(5)` → `"apple"`<br>`map.Get(7)` → `null`<br>Map remains unchanged                 |
| `Contains(key)`   | Returns `true` if the map contains the key, `false` otherwise              | `map.Contains(10)` → `true`<br>Map remains unchanged                                       |
| `GetLength()`     | Returns the number of key-value pairs in the map                           | `map.GetLength()` → `3`<br>Map remains unchanged                                           |

## Summary: Map ADT and Key Type Support

When implementing a Map Abstract Data Type (ADT) that supports any key type, two key issues arise:

1. **Non-integer keys are not supported.**
2. **Arrays cannot be sized to support all possible integer keys.**

### Solution: Hash Codes

To handle non-integer key types, a **hash code** is used:
- A **hash code** is a fixed-size, non-negative integer that aims to uniquely identify a key.
- A **hash function** computes this hash code from a given key.
- Hash functions are typically tailored to specific data types.

