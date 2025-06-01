# Zigzag Level Order Traversal - Key Concepts

## 🧠 Core Idea
- Perform a normal BFS traversal using a queue.
- At each level, collect node values into a temporary list.
- Use a **LinkedList** to insert node values:
  - `addLast()` if left-to-right
  - `addFirst()` if right-to-left
- This allows reversing the order at each level **without changing queue logic**.

---

## ❗ Common Mistake to Avoid
> Changing the order of adding children to the queue (left/right) to simulate zigzag

### ❌ Incorrect:
```java
if (direction) {
    if (node.left != null) queue.add(node.left);
    if (node.right != null) queue.add(node.right);
} else {
    if (node.right != null) queue.add(node.right);
    if (node.left != null) queue.add(node.left);
}
```

### ✅ Correct:
```java
if (node.left != null) queue.add(node.left);
if (node.right != null) queue.add(node.right);

if (leftToRight)
    levelList.addLast(node.val);
else
    levelList.addFirst(node.val);
```

---

## 🔁 Zigzag Level Order - Summary
- **Queue traversal is always left to right**
- **Zigzag is applied only to how node values are collected per level**
- Use `LinkedList` to efficiently reverse value order on-the-fly

---

## ✅ Pro Tip
> Think: "Traversal stays consistent — only the level result zigzags."

This way, you’ll never confuse **child order** with **value collection order**.
