
# 📘 Merge Intervals – Interview Prep Guide

## 🔹 Problem Statement
Given an array of intervals where `intervals[i] = [start_i, end_i]`, merge all overlapping intervals and return an array of the non-overlapping intervals that cover all the intervals in the input.

---

## 🔹 Key Concepts

- **Sort the intervals** by their start time.
- **Scan linearly** to merge overlapping intervals.
- Use a custom sorting algorithm if library functions are not allowed.

---

## 🔹 Step 1: Sort the Intervals by Start Time

**Using Arrays.sort (allowed):**
```java
Arrays.sort(intervals, (a, b) -> Integer.compare(a[0], b[0]));
```

**Without library sort (custom quicksort):**
```java
public void quickSort(int[][] intervals, int low, int high) {
    if (low < high) {
        int pi = partition(intervals, low, high);
        quickSort(intervals, low, pi - 1);
        quickSort(intervals, pi + 1, high);
    }
}

private int partition(int[][] intervals, int low, int high) {
    int[] pivot = intervals[high];
    int i = low - 1;
    for (int j = low; j < high; j++) {
        if (intervals[j][0] <= pivot[0]) {
            i++;
            swap(intervals, i, j);
        }
    }
    swap(intervals, i + 1, high);
    return i + 1;
}

private void swap(int[][] intervals, int i, int j) {
    int[] temp = intervals[i];
    intervals[i] = intervals[j];
    intervals[j] = temp;
}
```

---

## 🔹 Step 2: Merge the Intervals

```java
public int[][] merge(int[][] intervals) {
    quickSort(intervals, 0, intervals.length - 1); // Use only if library sort not allowed

    List<int[]> merged = new ArrayList<>();

    for (int[] interval : intervals) {
        if (merged.isEmpty() || merged.get(merged.size() - 1)[1] < interval[0]) {
            merged.add(interval);
        } else {
            merged.get(merged.size() - 1)[1] =
                Math.max(merged.get(merged.size() - 1)[1], interval[1]);
        }
    }

    return merged.toArray(new int[merged.size()][]);
}
```

---

## 🔹 Time and Space Complexity

- **Time:**  
  - Sorting: O(n log n)  
  - Merging: O(n)  
  - **Overall:** O(n log n)

- **Space:**  
  - O(n) for output list

---

## 🔹 Edge Cases to Consider

- Empty input: `[]`
- One interval only
- Fully overlapping intervals (e.g., `[[1,10], [2,5], [3,6]]`)
- Non-overlapping intervals (e.g., `[[1,2], [3,4], [5,6]]`)
- Touching intervals (e.g., `[[1,2], [2,3]]`) → should merge
