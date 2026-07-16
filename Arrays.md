# Arrays

---

# Arrays

---

## 🟢 LC 27 - Remove Element

**Pattern:** Fast & Slow Pointer (Read & Write Pointer)

### 🎯 Recognition
- Remove elements **in-place**
- Order of remaining elements must be preserved
- O(1) extra space required

### 💡 Core Idea
- `i` scans every element.
- `k` points to the next position where a valid element should be written.
- Copy only elements that are **not equal** to `val`.
- Return `k` because it represents the **new length** of the valid portion of the array.

### 🧠 Algorithm
1. Initialize `k = 0`.
2. Traverse the array using `i`.
3. If `nums[i] != val`:
   - Copy `nums[i]` to `nums[k]`.
   - Increment `k`.
4. Return `k`.

### 💻 Code

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

### ⏱️ Complexity

| Complexity | Value |
|------------|-------|
| Time | **O(n)** |
| Space | **O(1)** |

### ⚠️ Mistake I Made
- Thought `return k` returned the modified array.
- Actually, the array is modified **in-place**. `k` only tells LeetCode how many elements are valid.

### 🔑 Interview Takeaway
Whenever the interviewer says:
- **"Remove in-place"**
- **"Maintain order"**
- **"Use O(1) extra space"**

Think of the **Fast & Slow Pointer (Read & Write Pointer)** pattern.

### 🔗 Related Problems
- LC 26 – Remove Duplicates from Sorted Array
- LC 283 – Move Zeroes
- LC 977 – Squares of a Sorted Array

### ✅ Revision Checklist

- [ ] Can I identify the pattern without hints?
- [ ] Can I explain why `k` is returned?
- [ ] Can I code it in under 3 minutes?
