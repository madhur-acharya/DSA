# Two Pointer Techniques

The **two-pointer technique** is an efficient way to solve array problems by using two indices (or pointers) to traverse the array. This reduces time complexity compared to brute force approaches.

## 1. Two Sum (Sorted Array)  
🔹 **Problem:** Given a **sorted** array and a target sum, find two numbers that add up to the target.  
🔹 **Approach:** Use two pointers—one at the start and one at the end—moving them towards each other based on the sum.  

### **Python Code**
```python
def two_sum_sorted(arr, target):
    left, right = 0, len(arr) - 1
    while left < right:
        curr_sum = arr[left] + arr[right]
        if curr_sum == target:
            return [left, right]
        elif curr_sum < target:
            left += 1
        else:
            right -= 1
    return []  # No pair found

arr = [1, 2, 3, 4, 6]
target = 6
print(two_sum_sorted(arr, target))  # Output: [1, 3]
```

## 2. Dutch National Flag Problem (Sort 0s, 1s, and 2s)
🔹 Problem: Given an array containing only 0s, 1s, and 2s, sort it in-place.
🔹 Approach: Use three pointers: low for 0s, mid for 1s, and high for 2s. Swap elements accordingly.

### **Python Code**
```
def sort_colors(arr):
    low, mid, high = 0, 0, len(arr) - 1
    while mid <= high:
        if arr[mid] == 0:
            arr[low], arr[mid] = arr[mid], arr[low]
            low += 1
            mid += 1
        elif arr[mid] == 1:
            mid += 1
        else:
            arr[mid], arr[high] = arr[high], arr[mid]
            high -= 1

arr = [2, 0, 2, 1, 1, 0]
sort_colors(arr)
print(arr)  # Output: [0, 0, 1, 1, 2, 2]
```

## 3. Container With Most Water
🔹 Problem: Given an array where arr[i] represents the height of a vertical line at position i, find two lines that form a container with the maximum water area.
🔹 Approach: Use two pointers—one at the beginning and one at the end—adjusting the pointer with the shorter height.

### **Python Code**
```
def max_area(heights):
    left, right = 0, len(heights) - 1
    max_water = 0
    while left < right:
        max_water = max(max_water, (right - left) * min(heights[left], heights[right]))
        if heights[left] < heights[right]:
            left += 1
        else:
            right -= 1
    return max_water

heights = [1, 8, 6, 2, 5, 4, 8, 3, 7]
print(max_area(heights))  # Output: 49
```

## 4. Trapping Rain Water
🔹 Problem: Given an array representing elevations, find how much rainwater can be trapped.
🔹 Approach: Use two pointers (left and right) and track max heights from both sides to determine trapped water.

### **Python Code**
```
def trap_rain_water(heights):
    if not heights:
        return 0
    left, right = 0, len(heights) - 1
    left_max, right_max = heights[left], heights[right]
    water = 0
    while left < right:
        if left_max < right_max:
            left += 1
            left_max = max(left_max, heights[left])
            water += max(0, left_max - heights[left])
        else:
            right -= 1
            right_max = max(right_max, heights[right])
            water += max(0, right_max - heights[right])
    return water

heights = [0, 1, 0, 2, 1, 0, 1, 3, 2, 1, 2, 1]
print(trap_rain_water(heights))  # Output: 6
```


# 


