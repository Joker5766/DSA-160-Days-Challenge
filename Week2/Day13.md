## Day 13: Smallest Positive Missing Number

**Problem**: You are given an integer array arr[]. Your task is to find the smallest positive number missing from the array.

**Approach**:
- Sort the array to arrange elements in ascending order.
- Initialize missNumber = 1 (smallest positive integer).
- Iterate through the array:
  - If element == missNumber, increment missNumber.
- Return missNumber after the loop as the smallest missing positive integer.

**Code**:
```java
import java.util.Arrays;

class Solution13 {
    public int missingNumber(int[] arr) {
        Arrays.sort(arr);
        int missNumber = 1;

        for (int element : arr) {
            if (element == missNumber) {
                missNumber++;
            }
        }
        return missNumber;
    }
}

public class Main {
    public static void main(String[] args) {
        int[] array = {-8, 0, -1, -4, -3};
        Solution13 box = new Solution13();
        System.out.println(box.missingNumber(array));
    }
}

```
![Day 13 Output](./Day13-Screenshot.png)
