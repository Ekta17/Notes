
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

```java
class MinHeap {
    int[] heap;
    int size;
    int capacity;

    MinHeap(int capacity) {
        this.capacity = capacity;
        this.size = 0;
        heap = new int[capacity];
    }

    int parent(int i) {
        return (i - 1) / 2;
    }

    int left(int i) {
        return 2 * i + 1;
    }

    int right(int i) {
        return 2 * i + 2;
    }
    ...
}
```


### 1. Build Heap
**Time Complexity:** `O(n)`

```java
void buildHeap(int[] arr) {
    heap = arr;
    size = arr.length;
    for (int i = (size - 2) / 2; i >= 0; i--) {
        minHeapify(i);
    }
}
```

### 2. Heapify (MinHeap)
**Time Complexity:** `O(log n)`

```java
void minHeapify(int i) {
    int smallest = i;
    int l = left(i);
    int r = right(i);

    if (l < size && heap[l] < heap[smallest])
        smallest = l;
    if (r < size && heap[r] < heap[smallest])
        smallest = r;

    if (smallest != i) {
        int temp = heap[i];
        heap[i] = heap[smallest];
        heap[smallest] = temp;
        minHeapify(smallest);
    }
}
```

### 3. Insert
**Time Complexity:** `O(log n)`

```java
void insert(int key) {
    if (size == capacity) return;
    heap[size] = key;
    int i = size;
    size++;

    while (i != 0 && heap[parent(i)] > heap[i]) {
        int temp = heap[i];
        heap[i] = heap[parent(i)];
        heap[parent(i)] = temp;
        i = parent(i);
    }
}
```

### 4. Get Min
**Time Complexity:** `O(1)`

```java
int getMin() {
    return heap[0];
}
```

### 5. Extract Min
**Time Complexity:** `O(log n)`

```java
int extractMin() {
    if (size <= 0) return Integer.MAX_VALUE;
    if (size == 1) return heap[--size];

    int root = heap[0];
    heap[0] = heap[--size];
    minHeapify(0);
    return root;
}
```

### 6. Decrease Key
**Time Complexity:** `O(log n)`

```java
void decreaseKey(int i, int newVal) {
        heap[i] = newVal;
        while (i != 0 && heap[parent(i)] > heap[i]) {
            int temp = heap[i];
            heap[i] = heap[parent(i)];
            heap[parent(i)] = temp;
            i = parent(i);
        }
    }
```

### 7. Delete
**Time Complexity:** `O(log n)`

```java
void deleteKey(int i) {
        decreaseKey(i, Integer.MIN_VALUE);
        extractMin();
    }
```

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

