# Monotonic Queue Interview Guide

A Monotonic Queue is a specialized data structure used in sliding window problems to efficiently track maximum or minimum values. It's built on top of a double-ended queue (Deque) and maintains elements in either increasing or decreasing order.

---

## 🚀 What is a Monotonic Queue?

A Monotonic Queue:

- Maintains elements in **monotonic (non-increasing or non-decreasing)** order
- Enables **O(1)** access to the max or min in a window
- Is often used in problems like **Sliding Window Maximum** or **Minimum**

---

## 🧱 Java Implementation (Reusable Class)

```java
import java.util.Deque;
import java.util.LinkedList;

public class MonotonicQueue {
    private Deque<Integer> deque = new LinkedList<>();

    public void push(int n) {
        while (!deque.isEmpty() && deque.getLast() < n) {
            deque.removeLast();
        }
        deque.addLast(n);
    }

    public int max() {
        return deque.getFirst();
    }

    public void pop(int n) {
        if (!deque.isEmpty() && deque.getFirst() == n) {
            deque.removeFirst();
        }
    }
}
```

---

## 🧠 Sliding Window Maximum Pattern

```java
public int[] maxSlidingWindow(int[] nums, int k) {
    MonotonicQueue mq = new MonotonicQueue();
    int[] result = new int[nums.length - k + 1];
    int ri = 0;

    for (int i = 0; i < nums.length; i++) {
        mq.push(nums[i]);

        // ✅ Remove old element if it's outside the window
        if (i >= k) {
            mq.pop(nums[i - k]);
        }

        // ✅ Start recording max once the window is full
        if (i >= k - 1) {
            result[ri++] = mq.max();
        }
    }

    return result;
}
```

---

## 🧠 How to Remember the Conditions

### 🔁 Use this mantra:

**"Push new → Pop old → Print max"**

### 🎯 Think in terms of the window:

- **Push new**: Always push the current element
- **Pop old**: If `i >= k`, remove the element that just left the window (index `i - k`)
- **Print max**: Once the window size is `k` or more (`i >= k - 1`), record the max

---

## 📌 Common Interview Use Cases

- Sliding Window Maximum
- Sliding Window Minimum (change to increasing queue)
- 132 Pattern detection
- Minimum in all subarrays of size k
- Stock span problems

---

## 🛠️ To Customize for Minimum:

Just reverse the comparator in `push()`:

```java
while (!deque.isEmpty() && deque.getLast() > n) {
    deque.removeLast();
}
```

---

## ✅ Final Notes

- Practice dry runs with small examples
- Focus on window boundaries and sliding logic
- Use the "Push → Pop → Print" mantra during coding interviews

