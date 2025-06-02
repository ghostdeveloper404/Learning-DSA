
# Day 4: Learning Hash Tables

## Overview
Today, I explored **hash tables**, a fundamental data structure used for efficient storage and retrieval of data. Topics covered included:

- **Hash Functions**: How they transform keys into indexes.
- **Sets**: Collections that store unique elements using hashing.
- **Maps**: Key-value pairs stored efficiently with hash tables.

---

## **Understanding Hash Tables**
### **1. Hash Functions**
A **hash function** converts a key into a numerical index where data is stored.

Example of a simple hash function:
```python
def simple_hash(key, size):
    return sum(ord(char) for char in key) % size

For the key `"apple"`:
- ASCII values: `'a' = 97, 'p' = 112, 'p' = 112, 'l' = 108, 'e' = 101`
- Sum = `530`
- If array size = `10`, then `530 % 10 = 0`
- `"apple"` is stored at **index 0**.

---

### **2. Handling Collisions**
Collisions occur when different keys hash to the same index.

#### **Chaining (Linked List Approach)**
Instead of overwriting values, a **list** stores multiple key-value pairs at the same index.

Example:
```python
class HashTable:
    def __init__(self, size):
        self.size = size
        self.table = [[] for _ in range(size)]  

    def insert(self, key, value):
        index = simple_hash(key, self.size)
        self.table[index].append((key, value))  

    def search(self, key):
        index = simple_hash(key, self.size)
        for stored_key, value in self.table[index]:
            if stored_key == key:
                return value  
        return None  

hash_table = HashTable(10)
hash_table.insert("apple", 5)
hash_table.insert("orange", 10)

print(hash_table.search("apple"))  # Output: 5
```

#### **Open Addressing (Linear Probing)**
If a collision occurs, find the next **empty slot**.

```python
def insert_linear_probe(table, key, value):
    index = simple_hash(key, len(table))
    while table[index] is not None:
        index = (index + 1) % len(table)  # Move to next slot
    table[index] = (key, value)

hash_table = [None] * 10
insert_linear_probe(hash_table, "apple", 5)
insert_linear_probe(hash_table, "orange", 10)

print(hash_table)
```

---

### **3. Sets and Maps**
#### **Sets**
- Store **unique elements** using hashing.
```python
unique_items = set()
unique_items.add("apple")
unique_items.add("banana")
unique_items.add("apple")  # Duplicate ignored
print(unique_items)  # Output: {'apple', 'banana'}
```

#### **Maps (Dictionaries)**
- Store **key-value pairs** using hashing.
```python
student_scores = {"Alice": 85, "Bob": 90}
print(student_scores["Alice"])  # Output: 85
```

---

### **Applications**
- **Databases**: Hashing speeds up queries.
- **Cryptography**: Secure hashing techniques.
- **Caching**: Faster access to frequently used data.

Example:
Imagine a **phone book** stored in a hash table:
| Name       | Hash Index | Phone Number |
|------------|-------------|--------------|
| John Doe   | 2           | 9876543210   |
| Jane Smith | 7           | 1234567890   |

Lookups become **O(1)** time complexity—extremely fast!

---

### **Conclusion**
Mastering hash tables enables **efficient data handling**, ensuring fast **searching, storing, and deleting** of elements!
