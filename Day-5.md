# **Day 5: Stacks & Queues**

## **Introduction**
Stacks and Queues are two fundamental data structures used to manage collections of data efficiently. They help in organizing and processing data based on specific rules. Understanding these structures is crucial for solving a variety of programming problems.

---

## **1. Stacks (LIFO - Last In, First Out)**

### **Concept**
A **Stack** follows the **LIFO** principle, meaning the last item inserted is the first to be removed—just like stacking plates or books on top of each other.

### **Operations**
1. `push(item)`: Adds an item to the top of the stack.
2. `pop()`: Removes and returns the top item.
3. `peek()`: Returns the top item without removing it.
4. `is_empty()`: Checks if the stack is empty.
5. `size()`: Returns the number of items in the stack.

### **Implementation in Python**
Using a **list**:
```python
class Stack:
    def __init__(self):
        self.stack = []

    def push(self, item):
        self.stack.append(item)

    def pop(self):
        return self.stack.pop() if not self.is_empty() else None

    def peek(self):
        return self.stack[-1] if not self.is_empty() else None

    def is_empty(self):
        return len(self.stack) == 0

    def size(self):
        return len(self.stack)

# Example Usage
s = Stack()
s.push(1)
s.push(2)
s.push(3)
print(s.pop())  # Output: 3
print(s.peek()) # Output: 2
print(s.is_empty()) # Output: False
```

### **Applications of Stacks**
- **Function Calls & Recursion:** Keeps track of function execution order.
- **Undo/Redo Mechanism:** Used in text editors for reverting changes.
- **Expression Evaluation:** Used in converting infix expressions to postfix/prefix notation.
- **Backtracking Algorithms:** Used in solving mazes, puzzles, and graph traversal.

---

## **2. Queues (FIFO - First In, First Out)**

### **Concept**
A **Queue** follows the **FIFO** principle, meaning the first item inserted is the first to be removed—similar to a queue at a ticket counter.

### **Operations**
1. `enqueue(item)`: Adds an item to the end of the queue.
2. `dequeue()`: Removes and returns the front item.
3. `front()`: Returns the front item without removing it.
4. `is_empty()`: Checks if the queue is empty.
5. `size()`: Returns the number of items in the queue.

### **Implementation in Python**
Using `collections.deque` (preferred for efficiency):
```python
from collections import deque

class Queue:
    def __init__(self):
        self.queue = deque()

    def enqueue(self, item):
        self.queue.append(item)

    def dequeue(self):
        return self.queue.popleft() if not self.is_empty() else None

    def front(self):
        return self.queue[0] if not self.is_empty() else None

    def is_empty(self):
        return len(self.queue) == 0

    def size(self):
        return len(self.queue)

# Example Usage
q = Queue()
q.enqueue(1)
q.enqueue(2)
q.enqueue(3)
print(q.dequeue()) # Output: 1
print(q.front()) # Output: 2
print(q.is_empty()) # Output: False
```

### **Applications of Queues**
- **Task Scheduling:** Used in CPU scheduling and printing jobs.
- **Breadth-First Search (BFS):** Essential in graph traversal algorithms.
- **Data Buffering:** Used in streaming and networking to manage data flow.
- **Message Queues:** Helps in asynchronous communication between processes.

---

## **3. Variations of Stacks & Queues**
### **Stack Variants**
- **Monotonic Stack**: Used in optimization problems.
- **Two Stacks in an Array**: Efficient space utilization technique.

### **Queue Variants**
- **Circular Queue**: Prevents memory wastage in static arrays.
- **Priority Queue (Heap-Based)**: Processes elements based on priority instead of order.

---

## **4. Choosing Between Stack and Queue**
| Feature      | Stack (LIFO) | Queue (FIFO) |
|-------------|-------------|-------------|
| Access Order | Last added, first removed | First added, first removed |
| Example Usage | Function calls, undo/redo, recursion | Scheduling, buffering, graph traversal |
| Operations | `push()`, `pop()`, `peek()` | `enqueue()`, `dequeue()`, `front()` |
| Real-Life Analogy | Stack of books, browser history | Waiting line, messaging system |

---

## **Conclusion**
Stacks and Queues are essential for organizing and processing data efficiently. They have diverse applications in programming, from recursion management to real-world scheduling problems. By mastering these structures, you’ll be well-equipped to tackle a wide range of coding challenges.
