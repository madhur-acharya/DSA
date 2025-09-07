# Kaden's Algorithm
Kadane's Algorithm is used to find the contiguous subarray (containing at least one number) which has the largest sum and returns its sum.

## TLDR;
The idea is to loop through the array computing the prefix sum as you go along. 
At each index, if the previous prefix sum is <= current value, then start fresh from that index.

## Steps
- Initialize `current_max` and `global_max` to the first element of the array (or negative infinity if the array can contain all negative numbers and an empty subarray is not allowed).
- Iterate through the array starting from the second element:
- For each element, update `current_max` by taking the maximum of the current element itself and the sum of the current element plus the previous `current_max`. This means `current_max` = max(element, `current_max` + element).
- Update `global_max` by taking the maximum of `global_max` and `current_max`. This means `global_max` = max(`global_max`, `current_max`).
- After iterating through the entire array, `global_max` will hold the maximum sum of any contiguous subarray.

## Python Code 

```
def maxSubarraySum(arr):
    res = arr[0]
  
    # Outer loop for starting point of subarray
    for i in range(len(arr)):
        currSum = 0
      
        # Inner loop for ending point of subarray
        for j in range(i, len(arr)):
            currSum = currSum + arr[j]
          
            # Update res if currSum is greater than res
            res = max(res, currSum)
          
    return res
```

### Using Dynamic programming
```
def find_largest_subarray(arr, stt= 0):
    prev= arr[stt]
    start= stt
    end= stt
    for ix in range(stt+1, len(arr)):
        curr= prev + arr[ix]
        if arr[ix] > curr:
            return find_largest_subarray(arr, ix)
        
        if curr > prev:
            end= ix
        else:
            prev= curr
    return [start, end]

```
