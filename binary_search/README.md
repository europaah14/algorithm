# Binary Search Algorithm

A search algorithm to find the position of target in a **sorted data structure** (array/matrix)

## Version1: Find exact

Goal: find the position that equals to target

### Algorithm Notes

1. `start` and `end` are set as the first and last search position

2. `mid = (start + end) // 2` $\Rightarrow$ the middle point of the first and last search position

    * note when length `end - start + 1` is even, the midpoint is the one closer to `start` due to floor<br><br>

3. It needs to search for every possible positions, so while loop ends when `start > end`

4. update `start` and `end`

    - When `arr[mid] < target` $\Rightarrow$ `target` is after `mid` $\Rightarrow$ `start = mid + 1`

    - When `arr[mid] > target` $\Rightarrow$ `target` is before `mid` $\Rightarrow$ `end = mid - 1`

## Version2: Find closest

### Algorithm Notes

1. The logics of the 4 scenarios above are similar, all them of will **make a modification** (compared to Version1) when **searched the index which meets the requirement**

    i. when `arr[mid] > target` $\Rightarrow$ there can be potential answer before `mid` $\Rightarrow$ `end = mid`

    ii. when `arr[mid] == target` $\Rightarrow$ there can be potential answer before `mid` $\Rightarrow$ `end = mid`

    iii. when `arr[mid] < target` $\Rightarrow$ there can be potential answer after `mid` $\Rightarrow$ `start = mid`

    iv. when `arr[mid] == target` $\Rightarrow$ there can be potential answer after `mid` $\Rightarrow$ `start = mid`

2. the loop end when `start == end` which prevents dead loop

    - potential answer will be kept (`start = mid` or `end = mid`)
    
    - when `start == end`, `start` or `end` will never move further if `arr[mid]` meets the requirement

3. Difference between scenario 1 & 2 (find first index / leftmost) and scenario 3 & 4 (find last index / rightmost)

    - finding first index

        - when there are only 2 indices left, the midpoint has to be `start` to prevent dead loop

        - since we will set `end = mid` if `arr[mid]` meets the requirement $\Rightarrow$ loop is dead if `mid = end`

    - finding last index

        - when there are only 2 indices left, the midpoint has to be `end` to prevent dead loop

        - since we will set `start = mid` if `arr[mid]` meets the requirement $\Rightarrow$ loop is dead if `mid = start`