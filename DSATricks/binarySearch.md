#Binary Search

### **Find mid element**
🔹 ```mid = low + (high-low)/2```
- In languages like Java, where integer overflow can happen if the sum of two large integers exceeds the maximum value of an int.
- Why the optimal way works:
  - ```high - low``` ensures that you never exceed the max integer limit
  - Adding ```low``` back shifts the midpoint correctly within the range.
- Memory trick - ***Mid is Low plus half the distance.***
