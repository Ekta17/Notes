
# 📌 Two Pointer Pattern — Notes

## ✅ When to Use the Two Pointer Technique
Use the Two Pointer pattern when:
- The problem involves a **sorted array or linked list**.
- You need to find **pairs** or **subarrays** that satisfy a condition.
- The problem needs **in-place processing** with O(1) extra space.
- You need to **compare elements** from opposite ends or maintain a window.
- You need to **remove or skip duplicates** efficiently.

## ⚙️ How the Pattern Works
- **Initialize two pointers:** Usually `left` at the start and `right` at the end.
- **Move them towards each other:**
  - Move `left` forward (`left++`) to increase value or skip.
  - Move `right` backward (`right--`) to decrease value or skip.
- Stop when `left >= right`.

## 🔍 Classic Applications
| Problem | Pattern |
|---|---|
| Check if array has a pair with target sum (in sorted array) | `left` and `right` sum |
| Reverse an array in-place | Swap `left` and `right` |
| Palindrome check (string or linked list) | Compare `left` and `right` |
| Remove duplicates in-place | Use `slow` and `fast` pointer variant |
| Find container with most water | Shrink window from larger side |

## ⚡ Common Variations
- **Opposite Ends:** Classic `left` and `right` moving inward.
- **Fast & Slow:** One pointer moves faster — used in cycle detection.
- **Sliding Window:** Both pointers start together; `right` expands window, `left` shrinks it.

## 🗒️ Useful Tips
✅ Works best with sorted input.  
✅ Great for problems asking for **pairs, triplets, or subarrays**.  
✅ Helps achieve **O(n)** time where naive solution is **O(n²)**.  
✅ Watch out for off-by-one errors: `while (left < right)` vs `while (left <= right)`.

## 📚 Example Template (Java)

```java
// Example: Find if sorted array has a pair that sums to target
boolean hasPair(int[] nums, int target) {
    int left = 0, right = nums.length - 1;
    while (left < right) {
        int sum = nums[left] + nums[right];
        if (sum == target) return true;
        else if (sum < target) left++;
        else right--;
    }
    return false;
}
```

## 🧩 Key Idea
➡️ **Leverage order and shrinking search space.**  
➡️ Avoid nested loops by moving pointers intelligently.
