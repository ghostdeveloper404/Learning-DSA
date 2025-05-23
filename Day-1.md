
# Day 1 - Time & Space Complexity 🚀

## **Understanding Time & Space Complexity**  
When writing code, we want our programs to be **fast** and use **less memory**.  
- **Time Complexity** measures how long an algorithm takes to run as input size increases.  
- **Space Complexity** measures how much memory an algorithm uses.  

## **Big-O Notation (📏 Measuring Efficiency)**  
Big-O notation helps us describe how an algorithm’s performance changes as input size grows. It **ignores constant factors** and focuses on overall growth patterns.

---

### **Common Complexity Types (From Fastest to Slowest)**  

#### **O(1) - Constant Time**  
The execution time **does not change** with input size.  
```python
def get_first_element(arr):
    return arr[0]  # Always takes the same time, no matter the array size
```
Example: Accessing any index in an array is **instant** (Direct lookup).

#### **O(log n) - Logarithmic Time**  
The input size **reduces at each step**, making it very efficient.  
```python
def binary_search(arr, target):
    left, right = 0, len(arr) - 1
    while left <= right:
        mid = (left + right) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return -1
```
Example: **Binary search** divides the search space in half each time, making it faster than linear search.

#### **O(n) - Linear Time**  
Execution time **grows proportionally** with input size.  
```python
def find_element(arr, target):
    for num in arr:
        if num == target:
            return True  # Takes longer as the array size increases
    return False
```
Example: **Looping through an array** to find an element checks each element one by one.

#### **O(n log n) - Log-Linear Time**  
More complex than linear time, often seen in efficient sorting.  
```python
def merge_sort(arr):
    if len(arr) <= 1:
        return arr
    mid = len(arr) // 2
    left = merge_sort(arr[:mid])
    right = merge_sort(arr[mid:])
    return merge(left, right)

def merge(left, right):
    result = []
    while left and right:
        if left[0] < right[0]:
            result.append(left.pop(0))
        else:
            result.append(right.pop(0))
    return result + left + right
```
Example: **Merge Sort** breaks the array into smaller parts recursively, then merges them back efficiently.

#### **O(n²) - Quadratic Time**  
Performance **slows down** drastically with larger inputs due to nested loops.  
```python
def find_pairs(arr):
    for i in range(len(arr)):
        for j in range(len(arr)):
            print(arr[i], arr[j])  # Iterates through all possible pairs
```
Example: **Nested loops** cause the number of operations to grow exponentially.

#### **O(2ⁿ) - Exponential Time**  
The **slowest** complexity, often seen in recursive solutions with multiple calls.  
```python
def fibonacci(n):
    if n <= 1:
        return n
    return fibonacci(n - 1) + fibonacci(n - 2)
```
Example: **Recursive Fibonacci** grows exponentially since each call triggers **two more** calls.

---

### **Space Complexity Explained**  
Space complexity refers to how much memory an algorithm uses.  
- **O(1) Space** → Uses a **fixed** amount of memory (Example: Swapping two values).  
- **O(n) Space** → Uses memory **proportional** to input size (Example: Storing extra arrays).  
- **O(n²) Space** → Uses memory that grows **quadratically** (Example: Storing a 2D matrix).  

```python
def store_numbers(n):
    arr = []  # Takes O(n) space since we store n elements
    for i in range(n):
        arr.append(i)
    return arr
```

---

### **Why is Big-O Important?**  
✅ Helps compare solutions efficiently  
✅ Guides developers to write optimized code  
✅ Prevents slow algorithms from causing performance issues  
✅ Used in **coding interviews**, competitive programming & large-scale applications  

