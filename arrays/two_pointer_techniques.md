# Two Pointer Techniques

The **two-pointer technique** is an efficient way to solve array problems by using two indices (or pointers) to traverse the array. This reduces time complexity compared to brute force approaches.

## 1. Two Sum (Sorted Array)  
🔹 **Problem:** Given a **sorted** array and a target sum, find two numbers that add up to the target.  
🔹 **Approach:** Use two pointers—one at the start and one at the end—moving them towards each other based on the sum.  


### 🔹 Approach
- Use **two pointers**:
  - One pointer at the **start** of the array.
  - One pointer at the **end** of the array.
- In each step:
  - Add the values at both pointers.
  - If the sum equals the target, return the indices.
  - If the sum is **less than** the target, move the left pointer to the right to increase the sum.
  - If the sum is **greater than** the target, move the right pointer to the left to decrease the sum.
- Continue until the two pointers meet.

This works efficiently because the array is already sorted.

---

## 2. Dutch National Flag Problem (Sort 0s, 1s, and 2s)
🔹 Problem: Given an array containing only 0s, 1s, and 2s, sort it in-place.
🔹 Approach: Use three pointers: low for 0s, mid for 1s, and high for 2s. Swap elements accordingly.

### 🔹 Approach
- Use **three pointers**: `low`, `mid`, and `high`.
- `low` points to the position where the next `0` should go.
- `mid` scans through the array.
- `high` points to the position where the next `2` should go.
- Traverse the array:
  - If the current element is `0`, swap it with the element at `low` and move both `low` and `mid` forward.
  - If the current element is `1`, just move `mid` forward.
  - If the current element is `2`, swap it with the element at `high` and move `high` backward.
- Continue this process until `mid` passes `high`.

This way, all `0s` are moved to the beginning, `1s` to the middle, and `2s` to the end in a single pass.

---

## 3. Container With Most Water
🔹 Problem: Given an array where arr[i] represents the height of a vertical line at position i, find two lines that form a container with the maximum water area.
🔹 Approach: Use two pointers—one at the beginning and one at the end—adjusting the pointer with the shorter height.

### 🔹 Approach
- One pointer at the **beginning** of the array.
- One pointer at the **end** of the array.
- The idea is to maximize the area formed between the two lines.
- In each step:
  - Compare the heights at both pointers.
  - Move the pointer pointing to the **shorter line** inward.
- Keep doing this until the two pointers meet.

---

## 4. Trapping Rain Water
🔹 Problem: Given an array representing elevations, find how much rainwater can be trapped.
🔹 Approach: Use two pointers (left and right) and track max heights from both sides to determine trapped water.

### 🔹 Approach 1
- For every index in the array, find the the highest point to the left and the highest point to the right.
- To do that, loop over the array 3 times and save the left highest and right highest in 2 seperate arrays.
- Loop over the arrays one last time and calculate the area of water trapped for every index.

### 🔹 Approach 2
- Find to points which have water trapped between them, and the water is cut off from the rest of the points outside the range. This creates sections which can be solved independantly.
- For each section, The amount of water trapped is = (the total area of the section - the sum of hights of all points in the section)
- To calculate the area of the section, calculate the hight of the water level for that section (Call it H), and calculate the width of the section (call it L). A = H * L.
- WT = (H * L) - ∑ array[0]
- The full amount of water trapped is just sum of water trapped within each section. W = ∑ WT(a)

### 🔹 Approach 2
- This technique involves calculating the water trapped in horizontal slices from the bottom up.
- Keep an stack to hold the peaks from the left side.
- Keep a global variable for the total water accumulated.
- Loop over array from left:
- When array heights are falling, keep pushing the hights onto the stack.
- When heights start rising, pop the hights from the stack that are <= current hight and calculate water trapped for that range. Add to the global sum.
- Once finished looping over array, the global sum is the final answer

---




