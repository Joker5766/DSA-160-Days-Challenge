## Day 23: Reverse Pairs

**Problem**: Given an integer array nums, return the number of reverse pairs in the array.
**Approach**: Short Approach
1. Divide the Array:
    - Use merge sort to split the array into smaller subarrays.

2. Count Reverse Pairs During Merge:
    - For each element in the left subarray, count how many elements in the right subarray satisfy
        “left[i]>2×right[j]” using a pointer (j).

3. Merge the Subarrays:
    - Merge the two sorted subarrays while maintaining sorted order.

4. Combine the Results:
    - Total reverse pairs = reverse pairs in left + right + across left and right.


- Time Complexity: O(nlogn)
- Space Complexity: O(n)


**Code**:
```kotlin
class Y_DSA23 {
    var count = 0
    fun reversePairs(nums: IntArray): Int {
        mergeSort(nums, 0, nums.size - 1)
        return count
    }

    private fun mergeSort(nums: IntArray, start: Int, end: Int): IntArray {
        if (start >= end) {
            return intArrayOf(nums[start])
        }

        val mid = start + (end - start) / 2
        val left = mergeSort(nums, start, mid)
        val right = mergeSort(nums, mid + 1, end)

        return mergeAndCount(left, right)
    }

    private fun mergeAndCount(left: IntArray, right: IntArray): IntArray {
        var i = 0
        var j = 0
        val sorted = mutableListOf<Int>()

        for (l in left.indices) {
            while (j < right.size && left[l] > 2L * right[j]) {
                j++
            }
            count += j
        }

        i = 0
        j = 0

        while (i < left.size && j < right.size) {
            if (left[i] <= right[j]) {
                sorted.add(left[i])
                i++
            } else {
                sorted.add(right[j])
                j++
            }
        }

        while (i < left.size) {
            sorted.add(left[i])
            i++
        }

        while (j < right.size) {
            sorted.add(right[j])
            j++
        }

        return sorted.toIntArray()
    }
}

fun main() {
    val array = intArrayOf(2,4,3,5,1)
    val box = Y_DSA23()
    println(box.reversePairs(array))
}

```
![Day 2 Output](./Day2-Screenshot.png)
