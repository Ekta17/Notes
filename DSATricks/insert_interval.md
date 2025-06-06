
# 📘 Insert Interval – Interview Prep Guide

## 🔹 Problem Statement
You are given a list of non-overlapping intervals sorted by start time. Insert a new interval into the list, merging if necessary.

[LeetCode Problem Link](https://leetcode.com/problems/insert-interval/)

---

## 🔹 Key Concepts

### ✅ Strategy:

1. **Add all intervals that end before the new interval starts.**
2. **Merge all overlapping intervals** with the new interval.
3. **Add all intervals that start after the new interval ends.**

---

## 🔹 Critical Overlap Condition

```java
while (i < n && intervals[i][0] <= newInterval[1])
```

### ❓ What does this mean?

We check:
- If the start of the current interval is **less than or equal** to the end of the new interval.

### ✅ Why is this enough?

Because we're scanning in order, we've already added intervals that come **entirely before** the new interval. So now we just need to check if the current interval **overlaps** the new one from the start side.

---

## 🔹 Code Implementation

```java
public int[][] insert(int[][] intervals, int[] newInterval) {
    List<int[]> result = new ArrayList<>();
    int i = 0;
    int n = intervals.length;

    // 1. Add intervals that come before the new interval
    while (i < n && intervals[i][1] < newInterval[0]) {
        result.add(intervals[i]);
        i++;
    }

    // 2. Merge overlapping intervals
    while (i < n && intervals[i][0] <= newInterval[1]) {
        newInterval[0] = Math.min(newInterval[0], intervals[i][0]);
        newInterval[1] = Math.max(newInterval[1], intervals[i][1]);
        i++;
    }
    result.add(newInterval); // Add the merged interval

    // 3. Add the rest of the intervals
    while (i < n) {
        result.add(intervals[i]);
        i++;
    }

    return result.toArray(new int[result.size()][]);
}
```

---

## 🔹 Time and Space Complexity

- **Time:** O(n) — Single pass through the intervals
- **Space:** O(n) — For storing result

---

## 🔹 Example

### Input
```
intervals = [[1,3],[6,9]]
newInterval = [2,5]
```

### Output
```
[[1,5],[6,9]]
```

---

## 🔹 Visual Breakdown

- `[1,3]` ends before `[2,5]` starts → merge → `[1,5]`
- `[6,9]` is after `[1,5]` → add as-is

Final: `[[1,5], [6,9]]`

---

Let me know if you want more interval problems summarized like this!
