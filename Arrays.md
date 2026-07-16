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
