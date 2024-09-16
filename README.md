# LEETCODE-Strings-539
Let's walk through a dry run of the provided code for the method `findMinDifference` from the `Solution` class.

### Objective:
The function aims to find the **minimum difference** between any two time points given in the `timePoints` list. Each time point is in a "HH:MM" format.

### Key Variables:
- `ans`: Stores the minimum difference found so far. Initialized to the maximum possible difference (`24 * 60` = 1440 minutes, which is the total minutes in a day).
- `first`: Tracks the earliest time point in minutes. Initialized to 1440.
- `bucket[]`: A boolean array of size 1440 (representing each minute in a day). Each index corresponds to a minute, and if a time point appears, that index is set to `true`.

### Dry Run Example:

Let's assume `timePoints = ["23:59", "00:00"]`.

1. **Initialization:**
   - `ans = 1440`
   - `first = 1440`
   - `bucket[]` is initialized with `false`.

2. **First Loop (TimePoint Processing):**
   We will iterate over each time in `timePoints`.

   - **TimePoint "23:59":**
     - Convert "23:59" to minutes:
       \[
       \text{num} = 23 \times 60 + 59 = 1439
       \]
     - Update `first`:
       \[
       \text{first} = \min(1440, 1439) = 1439
       \]
     - `bucket[1439] = true`.
     
   - **TimePoint "00:00":**
     - Convert "00:00" to minutes:
       \[
       \text{num} = 0 \times 60 + 0 = 0
       \]
     - Update `first`:
       \[
       \text{first} = \min(1439, 0) = 0
       \]
     - `bucket[0] = true`.

3. **Second Loop (Find Minimum Difference):**
   - **Initial Setup:**
     - `prev = first = 0`

   - **Iteration through the `bucket[]` array:**
     - Start from `i = first + 1 = 1` and check each bucket position.
     - At `i = 1439`, we find `bucket[1439] = true`, which corresponds to "23:59".
     - Update `ans`:
       \[
       \text{ans} = \min(1440, 1439 - 0) = 1
       \]
     - Update `prev = 1439`.

4. **Final Adjustment (Across Day Boundary):**
   - After the loop, compute the difference across midnight:
     \[
     \text{ans} = \min(1, 1440 - 1439 + 0) = 1
     \]

### Final Result:
The minimum time difference between "23:59" and "00:00" is **1 minute**, which the function returns.

### Summary of Dry Run:
For `timePoints = ["23:59", "00:00"]`, the function returns **1** as the minimum time difference.
