
# Heaps - Key Notes

## What is a Heap?
Heap is an implementation of a **PriorityQueue**.

Used in algorithms like:
- Dijkstra's algorithm
- Prim's algorithm
- Huffman encoding
- Priority scheduling

---

## Types of Heap

### MinHeap (or MaxHeap)
- **MinHeap:** Root is the smallest element.
- **MaxHeap:** Root is the largest element.
- Each subtree must also follow the heap condition.
- It’s a **complete binary tree**: all levels are completely filled from left to right.

---

## Array Representation

A binary heap is typically implemented using an array:

- `left child` of index `i` = `2*i + 1`
- `right child` of index `i` = `2*i + 2`
- `parent` of index `i` = `(i - 1) / 2`

**Tip to Remember:**
- Use level-order numbering.
- Children are always after the parent in the array.

---

## Java PriorityQueue
Java provides a built-in `PriorityQueue` class that is a MinHeap by default.

```java
PriorityQueue<Integer> minHeap = new PriorityQueue<>();
PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Collections.reverseOrder());
```

---

## Heap Operations and Java Implementations

### 1. Build Heap
**Time Complexity:** `O(n)`

```java
void buildHeap(int[] arr) {
    int n = arr.length;
    for (int i = (n - 2) / 2; i >= 0; i--) {
        heapify(arr, n, i);
    }
}
```

### 2. Heapify (MinHeap)
**Time Complexity:** `O(log n)`

```java
void heapify(int[] arr, int n, int i) {
    int smallest = i;
    int left = 2*i + 1;
    int right = 2*i + 2;

    if (left < n && arr[left] < arr[smallest])
        smallest = left;
    if (right < n && arr[right] < arr[smallest])
        smallest = right;

    if (smallest != i) {
        int temp = arr[i];
        arr[i] = arr[smallest];
        arr[smallest] = temp;
        heapify(arr, n, smallest);
    }
}
```

### 3. Insert
**Time Complexity:** `O(log n)`

```java
void insert(PriorityQueue<Integer> heap, int val) {
    heap.add(val);
}
```

### 4. Get Min
**Time Complexity:** `O(1)`

```java
int getMin(PriorityQueue<Integer> heap) {
    return heap.peek();
}
```

### 5. Extract Min
**Time Complexity:** `O(log n)`

```java
int extractMin(PriorityQueue<Integer> heap) {
    return heap.poll();
}
```

### 6. Decrease Key
- Not directly supported in `PriorityQueue`. Use a custom class with manual reordering or recreate the heap.

### 7. Delete
- Not directly supported in `PriorityQueue`. For custom heap, replace the element with last and call heapify.

---

## Key Tips to Remember

- Use bottom-up approach for building heap (start from last parent).
- Use top-down for inserting elements (bubble up).
- Use heapify when deleting/extracting min (bubble down).
- Heap is always a **complete binary tree**, never skewed.
- Arrays make heap **cache-friendly** and space-efficient.
- For `PriorityQueue`, think of `peek()` as `getMin()` and `poll()` as `extractMin()`.

---

## When to Use a Heap?

- When you need fast access to the minimum/maximum element.
- When sorting with limited space (HeapSort).
- When merging `k` sorted arrays.
- For scheduling problems (CPU scheduling, event queues).

