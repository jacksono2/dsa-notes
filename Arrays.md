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

**Related**
- LC 26
- LC 283
- LC 977
