# 📘 Arrays

---

## 🟢 LC 27 - Remove Element

**Pattern:** Fast & Slow Pointer

**Recognition**
- In-place modification
- Maintain order
- O(1) extra space

**Idea**
- `i` → read pointer
- `k` → write pointer
- Copy only valid elements
- Return `k` (new length)

```java
class Solution {
    public int removeElement(int[] nums, int val) {
        int k = 0;

        for (int i = 0; i < nums.length; i++) {
            if (nums[i] != val) {
                nums[k] = nums[i];
                k++;
            }
        }

        return k;
    }
}
```

**Complexity**
- Time: `O(n)`
- Space: `O(1)`

**Mistake**
- `return k` → returns the new valid length, **not** the array.

## 🟢 LC 1672 - Richest Customer Wealth

**Pattern:** Array Traversal

**Trigger**
- 2D array
- Find maximum row sum

**Idea**
- Traverse each row
- Calculate the sum of each customer's wealth
- Track the maximum sum

```java
class Solution {
    public int maximumWealth(int[][] accounts) {
        int maxWealth = 0;

        for (int i = 0; i < accounts.length; i++) {
            int wealth = 0;

            for (int j = 0; j < accounts[i].length; j++) {
                wealth += accounts[i][j];
            }

            maxWealth = Math.max(maxWealth, wealth);
        }

        return maxWealth;
    }
}
```

**Complexity**
- Time: `O(m × n)`
- Space: `O(1)`
