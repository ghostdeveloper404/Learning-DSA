
# Day 1 - Time & Space Complexity 🚀

## **What is Time & Space Complexity?**  
Time complexity measures **how fast** an algorithm runs, and space complexity measures **how much memory** it uses.  

## **Big-O Notation (📏 Efficiency Measurement)**  
Big-O notation describes how an algorithm scales with input size.

### **Common Complexity Levels with Code Examples:**

#### **O(1) - Constant Time**  
No matter the input size, execution time stays the same.  

```python
def get_first_element(arr):
    return arr[0]  # Always takes the same time
```

#### **O(log n) - Logarithmic Time**  
Input size reduces in each step _(Binary Search)_.  

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

#### **O(n) - Linear Time**  
Execution time grows **proportionally** with input size.  

```python
def find_element(arr, target):
    for num in arr:
        if num == target:
            return True  # Takes longer for larger arrays
    return False
```

#### **O(n²) - Quadratic Time**  
Nested loops make execution slower for large inputs.  

```python
def find_pairs(arr):
    for i in range(len(arr)):
        for j in range(len(arr)):
            print(arr[i], arr[j])  # Iterates through all pairs
```

## **Why is Big-O Important?**  
✅ Helps compare solutions easily  
✅ Guides better coding choices for efficiency  
✅ Prevents slow algorithms  


