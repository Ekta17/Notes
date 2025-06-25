# 🧠 Guide to Sorting in Interval Problems

Interval problems often require sorting to simplify comparisons and identify overlaps. Here's a cheat sheet to remember **when to sort by start time** vs **end time**.

---

## 📌 1. Non-Overlapping Intervals (LeetCode 435)

### ❓ Problem:

Remove the minimum number of intervals to make the rest non-overlapping.

### ✅ Sort by: **End Time (Ascending)**

### 💡 Why:

- Greedily choose the interval that ends the earliest.
- Leaves room for more intervals in the future (maximizes count).

### 🔁 Pattern:

```java
Arrays.sort(intervals, (a, b) -> Integer.compare(a[1], b[1]));
```

---

## 📌 2. Merge Intervals (LeetCode 56)

### ❓ Problem:

Merge all overlapping intervals into one.

### ✅ Sort by: **Start Time (Ascending)**

### 💡 Why:

- Makes it easy to compare current interval with the previous one.
- If current.start <= previous.end → they overlap → merge.

### 🔁 Pattern:

```java
Arrays.sort(intervals, (a, b) -> Integer.compare(a[0], b[0]));
```

---

## 📌 3. Insert Interval (LeetCode 57)

### ❓ Problem:

Insert a new interval and merge as needed.

### ✅ Sort by: **Start Time (if not already sorted)**

### 💡 Why:

- Insertion happens in order.
- Merge logic requires comparing start/end sequentially.

---

## 🧠 Summary Table

| Problem Type            | Sort By               | Reason                                                |
| ----------------------- | --------------------- | ----------------------------------------------------- |
| Erase Overlap Intervals | End Time              | Greedy: earliest finish allows more intervals         |
| Merge Intervals         | Start Time            | Easy sequential merging                               |
| Insert Interval         | Start Time            | Ordered insert and merge                              |
| Meeting Rooms I/II      | Start Time / End Time | Depends on what you're checking (room count, clashes) |

---

## 🏁 Pro Tip:

If your goal is to **maximize the number of non-overlapping intervals**, always sort by **end time**. If your goal is to **merge or build a timeline**, sort by **start time**.

---

Let me know if you'd like this as a PDF or cheat sheet version!

