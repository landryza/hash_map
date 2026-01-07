***

# Hash Map Implementations in Python

This repository contains two complete hash map implementations written from scratch in Python, each using a different collision resolution strategy:

1.  **Open Addressing with Quadratic Probing**
2.  **Separate Chaining with Linked Lists**

Both implementations avoid Python’s built-in `dict` and instead rely on custom data structures to demonstrate a deep understanding of hashing mechanics, collision handling, resizing, and performance trade-offs.

***

## Project Structure

    .
    ├── hash_map_quadratic_sc.py
    ├── hash_map_separate_oa.py
    ├── a6_include.py
    └── README.md

***

## Core Concepts Demonstrated

*   Hash functions and key distribution
*   Collision resolution strategies
*   Load factor management
*   Dynamic resizing and rehashing
*   Trade-offs between time, space, and complexity
*   Iterator support and full CRUD operations

***

## Hash Map — Open Addressing (Quadratic Probing)

**File:** `hash_map_oa.py`

This implementation uses open addressing, meaning all key/value pairs are stored directly inside the hash table array.

### Collision Resolution

Quadratic probing is used when collisions occur:

    (hash(key) + j²) % capacity

Probing continues until an empty slot or the target key is found.

### Deletion Strategy

*   Uses tombstones to mark deleted entries.
*   Tombstones preserve probe chains and are reused during insertion.
*   Tombstones are ignored during resizing.

### Resizing Behavior

*   Table resizes when load factor ≥ 0.5.
*   Capacity is always adjusted to the next prime number.
*   All active entries are rehashed into the new table.

### Key Characteristics

*   Lower memory overhead (no secondary structures).
*   Cache-friendly due to contiguous storage.
*   Performance degrades at higher load factors.
*   Deletion logic is more complex due to tombstones.

### Supported Operations

*   `put`
*   `get`
*   `remove`
*   `contains_key`
*   `resize_table`
*   `clear`
*   Iteration over active entries

***

## Hash Map — Separate Chaining

**File:** `hash_map_separate_chaining.py`

This implementation uses separate chaining, where each index in the hash table contains a linked list of key/value pairs.

### Collision Resolution

*   Colliding keys are stored in the same bucket.
*   Each bucket is implemented as a `LinkedList`.

### Resizing Behavior

*   Table resizes when load factor ≥ 1.0.
*   Capacity is always adjusted to the next prime number.
*   All key/value pairs are rehashed into the new table.

### Key Characteristics

*   Handles high load factors gracefully.
*   Simpler deletion logic (remove from linked list).
*   Slightly higher memory usage due to linked structures.
*   Less cache-friendly than open addressing.

### Supported Operations

*   `put`
*   `get`
*   `remove`
*   `contains_key`
*   `resize_table`
*   `clear`
*   `get_keys_and_values`

***

## Additional Functionality

### `find_mode` (Separate Chaining Version)

The separate chaining implementation includes a `find_mode` function that:

*   Counts string frequencies using the hash map.
*   Returns all values with the highest frequency.
*   Demonstrates real-world use of hashing for frequency analysis.

***

## Technologies Used

*   **Python 3**
*   Custom implementations of:
    *   Dynamic arrays
    *   Linked lists
*   No external libraries
*   No use of Python’s built-in `dict`

***

## How to Run

Clone the repository:

```bash
git clone https://github.com/your-username/your-repo-name.git
cd your-repo-name
```

Run either implementation:

```bash
python hash_map_oa.py
python hash_map_sc.py
```

Each file includes a comprehensive test suite demonstrating correctness and edge cases.

***

## Why This Project?

This project was built to:

*   Explore and compare two fundamental hash table designs.
*   Reinforce understanding of collision resolution strategies.
*   Demonstrate data-structure fundamentals commonly tested in interviews.
*   Serve as a clear, well-documented portfolio example.

***
