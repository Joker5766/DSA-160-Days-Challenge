## Day 9: Minimize the Heights II

**Problem**: Given an array arr[] denoting heights of N towers and a positive integer K.
- For each tower, you must perform exactly one of the following operations exactly once.
      - Increase the height of the tower by K
      - Decrease the height of the tower by K
- Find out the minimum possible difference between the height of the shortest and tallest towers after you have modified each tower.

**Approach**:
1. Sort the Array:
  - Sorting helps compare heights systematically.

2. Initial Difference:
  - Calculate the initial difference between the tallest (arr[j]) and shortest (arr[0]) towers.

3. Adjust Heights:
  - For each tower (except the first), ensure subtracting K doesn’t make the height negative.
    - Compute:
      - Minimum height: Smallest after adjustments.
      - Maximum height: Largest after adjustments.

4. Update Difference:
  - Track the minimum difference between MaxHeight and MinHeight.

5. Return the Result:
  - Output the smallest difference after all iterations.

**Code**:
```java
import java.util.Arrays;

class Solution9 {
    int getMinDiff(int[] arr, int k) {
        Arrays.sort(arr);
        int j = arr.length - 1;
        int value = arr[j] - arr[0];
        for (int i = 1; i <= j; i++){
            if (arr[i] - k < 0){
                continue;
            }
            int MinHeight = Math.min(arr[0] + k, arr[i] - k);
            int MaxHeight = Math.max(arr[i-1] + k, arr[j] - k);

            value = Math.min(value, MaxHeight - MinHeight);
        }
        return value;
    }
}

public class Problem9 {
    public static void main(String[] args) {
        int[] array = {3, 9, 12, 16, 20};
        int k = 3;
        Solution9 box = new Solution9();
        System.out.println(box.getMinDiff(array, k));
    }
}


```
![Day 9 Output](./Day9-Screenshot.png)
