## Day 26: Number of occurrence

**Problem**: Given a sorted array, arr[] and a number target, you need to find the number of occurrences of target in arr[].

**Approach**: 
Just Simple Approach:
    - Use for loop and a container to store count of occurrence
    - Loop through array and count the occurrence
    - Return the count

**Code**:
```kotlin
class Solution {
    int countFreq(int[] arr, int target) {
        int count = 0;
        for(int i = 0; i < arr.length; i++){
            if(arr[i] == target) count++;
        }
        return count;
    }
}

```
![Day 26 Output](./Day26-Screenshot.png)
