# 🧠 How to Remember Prefix and Suffix Product Calculations (Leetcode: Product of Array Except Self)

This guide helps you remember how to solve the classic problem **"Product of Array Except Self"** using prefix and suffix products — without using division.

---

## ✅ The Problem Recap

> Given an array `nums`, return an array `output` where:
>
> `output[i] = product of all elements in nums except nums[i]`
>
> ❗ Constraints:
> - No division
> - O(n) time
> - O(1) extra space (output array doesn’t count)

---

## 🧠 High-Level Trick:

> At each index `i`, the result is:
> 
> **Product of all elements to the *left* of `i` × Product of all elements to the *right* of `i`**

---

## 🔑 Memory Hack: “🏃 Walk Forward, Walk Backward”

- **Walk forward** → compute **prefix products**
- **Walk backward** → apply **suffix products**

---

## ▶️ Prefix Calculation (Left ➝ Right)

```java
output[0] = 1;
for (int i = 1; i < n; i++) {
    output[i] = output[i - 1] * nums[i - 1];
}
```

💬 Say to yourself:
> “To get product before me, I take what was before and multiply by the previous number.”

Example for `nums = [1, 2, 3, 4]`:
```
prefix = [1, 1, 2, 6]
```

---

## ◀️ Suffix Calculation (Right ➝ Left)

```java
int suffix = 1;
for (int i = n - 1; i >= 0; i--) {
    output[i] *= suffix;
    suffix *= nums[i];
}
```

💬 Say to yourself:
> “I already have everything to the left from prefix. Now multiply by what's coming from the right.”

Example:
```
suffix goes: 1 → 4 → 12 → 24
```

Final Output:
```
[24, 12, 8, 6]
```

---

## 🔁 Quick Recap to Say Before Interviews

1. **Prefix pass:**
   - `output[0] = 1`
   - `output[i] = output[i-1] * nums[i-1]`

2. **Suffix pass:**
   - `suffix = 1`
   - `output[i] *= suffix`
   - `suffix *= nums[i]`

---

## 🧮 Visual Model

| Index | Prefix (left product) | Suffix (right product) | Output[i] = Prefix × Suffix |
|-------|------------------------|-------------------------|------------------------------|
| 0     | 1                      | 2×3×4 = 24              | 1 × 24 = 24                  |
| 1     | 1                      | 3×4 = 12                | 1 × 12 = 12                  |
| 2     | 1×2 = 2                | 4                       | 2 × 4 = 8                    |
| 3     | 1×2×3 = 6              | 1                       | 6 × 1 = 6                    |

---

## 📦 Final Mnemonic:

### “Prefix pushes from Left. Suffix sweeps from Right.”

- Prefix pass: Left ➝ Right
- Suffix pass: Right ➝ Left

---

## ✅ Done!

Now you have a fast mental model for this classic problem!