# Binary Search Algorithm

A search algorithm to find the position of target in a **sorted data structure** (array/matrix)

## Version1: Find exact

**Goal**: find the position that equals to target

### Algorithm Notes

1. `start` and `end` are set as the first and last search position

2. `mid = (start + end) // 2` $\Rightarrow$ the middle point of the first and last search position

    * note when length `end - start + 1` is even, the midpoint is the one closer to `start` due to floor

3. It needs to search for every possible positions, so while loop ends when `start > end`

4. update `start` and `end`

    - When `arr[mid] < target` $\Rightarrow$ `target` is after `mid` $\Rightarrow$ `start = mid + 1`

    - When `arr[mid] > target` $\Rightarrow$ `target` is before `mid` $\Rightarrow$ `end = mid - 1`

## Version2: Find closest

