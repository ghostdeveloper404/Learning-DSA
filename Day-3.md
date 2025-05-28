
## **Linked Lists: An Overview**
A **linked list** is a linear data structure where elements are stored in nodes, and each node contains a reference (or pointer) to the next node in the sequence. Unlike arrays, linked lists don't require contiguous memory allocation and can dynamically grow or shrink.

### **Why Use Linked Lists?**
1. **Dynamic Memory Allocation:** Unlike arrays, linked lists can expand or contract dynamically.
2. **Efficient Insertions & Deletions:** Elements can be easily inserted or deleted without shifting other elements.
3. **Memory Utilization:** Allocates memory only when needed, reducing wasted space.

---

## **Singly Linked List (SLL)**
A **Singly Linked List** consists of nodes, each containing:
1. **Data** (the value stored)
2. **Pointer to the next node**

### **Structure of a Singly Linked List Node**
```python
class Node:
    def __init__(self, data):
        self.data = data  # Value stored in node
        self.next = None  # Pointer to the next node
```

### **Basic Operations**
#### **Insertion at End**
```python
class SinglyLinkedList:
    def __init__(self):
        self.head = None  # First node (initially empty)

    def append(self, data):
        new_node = Node(data)  # Create a new node
        if not self.head:  # If list is empty, set new_node as head
            self.head = new_node
            return
        
        temp = self.head
        while temp.next:  # Traverse till the last node
            temp = temp.next
        temp.next = new_node  # Attach new_node at the end
```

#### **Deletion (Specific Data)**
```python
    def delete(self, key):
        temp = self.head
        
        # If the node to delete is the head
        if temp and temp.data == key:
            self.head = temp.next
            temp = None
            return
        
        prev = None
        while temp and temp.data != key:
            prev = temp
            temp = temp.next
        
        if temp is None:
            return  # Element not found
        
        prev.next = temp.next
        temp = None  # Delete the node
```

### **Advantages of Singly Linked List**
✅ Uses less memory compared to doubly linked lists \
✅ Efficient insertions/deletions compared to arrays \
✅ No predefined size constraint

### **Disadvantages**
❌ Cannot be traversed backward \
❌ Searching is slower (O(n)) compared to arrays (O(1) for direct indexing)

---

## **Doubly Linked List (DLL)**
A **Doubly Linked List** consists of nodes, each containing:
1. **Data** (value stored)
2. **Pointer to the previous node**
3. **Pointer to the next node**

### **Structure of a Doubly Linked List Node**
```python
class Node:
    def __init__(self, data):
        self.data = data
        self.prev = None  # Pointer to previous node
        self.next = None  # Pointer to next node
```

### **Basic Operations**
#### **Insertion at End**
```python
class DoublyLinkedList:
    def __init__(self):
        self.head = None

    def append(self, data):
        new_node = Node(data)
        if not self.head:  # If list is empty
            self.head = new_node
            return
        
        temp = self.head
        while temp.next:  # Traverse till the last node
            temp = temp.next
        temp.next = new_node
        new_node.prev = temp  # Connect new_node backward
```

#### **Deletion (Specific Data)**
```python
    def delete(self, key):
        temp = self.head
        
        # If node to delete is the head
        if temp and temp.data == key:
            self.head = temp.next
            if self.head:
                self.head.prev = None
            temp = None
            return
        
        while temp and temp.data != key:
            temp = temp.next
        
        if temp is None:
            return  # Element not found
        
        if temp.next:
            temp.next.prev = temp.prev
        if temp.prev:
            temp.prev.next = temp.next
        
        temp = None  # Delete the node
```

### **Advantages of Doubly Linked List**
✅ Can be traversed **both forward & backward** \
✅ Easier to delete nodes compared to SLL (no need to traverse twice) \
✅ More flexible compared to SLL

### **Disadvantages**
❌ Uses more memory due to extra pointer (`prev`) \
❌ Slightly slower insertion/deletion due to additional pointer updates

---

## **Comparison: SLL vs DLL**

| Feature              | Singly Linked List (SLL) | Doubly Linked List (DLL) |
|----------------------|-------------------------|---------------------------|
| Memory Usage        | Less                     | More (extra `prev` pointer) |
| Traversability      | One-way                  | Two-way |
| Ease of Deletion    | Moderate                 | Easier (direct access to prev & next) |
| Speed of Searching  | Slow (O(n))              | Same as SLL |

---

## **When to Use Which?**
- **Use SLL when:** Memory is a concern, and only forward traversal is needed.
- **Use DLL when:** You need **bidirectional** traversal or **fast deletions**.
