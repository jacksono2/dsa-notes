# 📘 Arrays

---

## 🟢 LC 27 • Remove Element

> **Pattern:** Fast & Slow Pointer

### 🎯 Recognition
- In-place modification
- Maintain order
- O(1) extra space

### 💡 Idea
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

### 📊 Complexity

| Time | Space |
|------|-------|
| `O(n)` | `O(1)` |

### ⚠️ Mistake
> `return k` → returns the new valid length, **not** the array.

---

## 🟢 LC 1672 • Richest Customer Wealth

> **Pattern:** Array Traversal

### 🎯 Trigger
- 2D array
- Find maximum row sum

### 💡 Idea
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

### 📊 Complexity

| Time | Space |
|------|-------|
| `O(m × n)` | `O(1)` |

---

## 🟢 LC 485 • Max Consecutive Ones

> **Pattern:** Array Traversal

### 🎯 Trigger
- Count consecutive elements
- Reset count when condition breaks

### 💡 Idea
- Traverse the array
- Increment count for every `1`
- Reset count when `0` is encountered
- Track the maximum count

```java
class Solution {
    public int findMaxConsecutiveOnes(int[] nums) {
        int count = 0;
        int maxCount = 0;

        for (int num : nums) {
            if (num == 1) {
                count++;
                maxCount = Math.max(maxCount, count);
            } else {
                count = 0;
            }
        }

        return maxCount;
    }
}
```

### 📊 Complexity

| Time | Space |
|------|-------|
| `O(n)` | `O(1)` |

### ⚠️ Mistake
> Forgetting to reset the count when `0` is encountered.

---

## 🟢 LC 1295 • Find Numbers with Even Number of Digits

> **Pattern:** Array Traversal

### 🎯 Trigger
- Process every element independently
- Count digits of a number

### 💡 Idea
- Traverse the array
- Count the number of digits in each number
- Increment answer if the digit count is even

```java
class Solution {
    public int findNumbers(int[] nums) {
        int evencount=0;
        int digit=0;
        for(int i=0;i<nums.length;i++){
            while(nums[i]!=0){
                digit++;
                nums[i]/=10;
            }
            if(digit%2==0){
                evencount++;
            }
            digit=0;
        }
        return evencount;
    }
}
```

### 📊 Complexity

| Time | Space |
|------|-------|
| `O(n)` | `O(1)` |

### ⚠️ Mistake
> Forgetting that digit count can also be found mathematically (`/10`) instead of converting to a string.

---

## 🟢 LC 26 - Remove Duplicates from Sorted Array

> **Pattern:** Slow & Fast Pointer (In-place Array Compression)

---

### 🎯 Trigger / Recognition

- Array is **sorted**
- Need to **remove duplicates in-place**
- Return the **number of unique elements**
- Extra space is **not allowed**

---

### 💡 Idea

- Use two pointers:
  - `i` → Fast pointer (scans every element)
  - `j` → Slow pointer (last unique element)
- If `nums[i] != nums[j]`:
  - Move `j` forward
  - Copy `nums[i]` to `nums[j]`
- Return `j + 1` (count of unique elements)

```java
class Solution {
    public int removeDuplicates(int[] nums) {
        int n = nums.length;
        int j = 0;

        for (int i = 1; i < n; i++) {
            if (nums[i] != nums[j]) {
                j++;
                nums[j] = nums[i];
            }
        }

        return j + 1;
    }
}
```

---

### ⚡ Complexity

| Operation | Complexity |
|-----------|------------|
| Time | **O(n)** |
| Space | **O(1)** |

---

### ⚠️ Mistake

> `j` is the **index of the last unique element**, **not the count**.  
> Therefore, return **`j + 1`**, not `j`.

---

## 🟢 LC 189 - Rotate Array

---

> **Pattern:** Array Reversal / In-place Rotation

---

### 🎯 Recognition

- Rotate an array to the **right by `k` steps**.
- `k` may be **greater than the array length**.
- Follow-up asks for an **O(1) space** solution.

---

### 💡 Idea

1. Reduce unnecessary rotations.
   ```java
   k = k % n;
   ```
2. Reverse the entire array.
3. Reverse the first `k` elements.
4. Reverse the remaining `n - k` elements.

---

### 💻 Code

```java
class Solution {
    public void rotate(int[] nums, int k) {
        int n = nums.length;
        k = k % n;

        reverse(nums, 0, n - 1);
        reverse(nums, 0, k - 1);
        reverse(nums, k, n - 1);
    }

    private void reverse(int[] nums, int left, int right) {
        while (left < right) {
            int temp = nums[left];
            nums[left] = nums[right];
            nums[right] = temp;
            left++;
            right--;
        }
    }
}
```

---

### 📊 Complexity

| Operation | Complexity |
|-----------|-----------:|
| ⏱️ Time | **O(n)** |
| 💾 Space | **O(1)** |

---

### ⚠️ Mistake

> - Forgetting `k = k % n`.
> - Reversing `0` to `n-k` instead of `0` to `k-1`.
> - Incorrect swap logic while reversing.
> - Defining `reverse()` inside `rotate()` (invalid in Java).

---

## 🟢 LC 88 • Merge Sorted Array

> **Pattern:** Two Pointers (Merge from End)

### 🎯 Trigger
- Two sorted arrays
- Merge **in-place**
- `nums1` has extra space at the end
- O(1) extra space required

### 💡 Idea
- Start from the **end** of both arrays.
- `i` → Last valid element in `nums1`
- `j` → Last element in `nums2`
- `k` → Last index of `nums1`
- Place the **larger element** at `nums1[k]`.
- Continue until all elements of `nums2` are merged.

```java
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int i = m - 1;
        int j = n - 1;
        int k = m + n - 1;

        while (j >= 0) {
            if (i < 0) {
                nums1[k] = nums2[j];
                j--;
                k--;
                continue;
            }

            if (nums1[i] < nums2[j]) {
                nums1[k] = nums2[j];
                j--;
            } else {
                nums1[k] = nums1[i];
                i--;
            }

            k--;
        }
    }
}
```

### 📊 Complexity

| Time | Space |
|------|-------|
| `O(m + n)` | `O(1)` |

### ⚠️ Mistake
> - Merging from the front instead of the back.
> - Forgetting the `i < 0` edge case.
> - Forgetting `continue`, leading to `nums1[-1]`.
> - Forgetting to decrement `k` after every placement.
> - Using an extra array instead of utilizing the empty space in `nums1`.

---
