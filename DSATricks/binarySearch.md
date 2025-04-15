#Binary Search

### **Find mid element**
🔹 ```mid = low + (high-low)/2```
- In languages like Java, where integer overflow can happen if the sum of two large integers exceeds the maximum value of an int.
- Why the optimal way works:
  - ```high - low``` ensures that you never exceed the max integer limit
  - Adding ```low``` back shifts the midpoint correctly within the range.
- Memory trick - ***Mid is Low plus half the distance.***

### **First occurrence of element in sorted array**
- Check mid if its the element and then if its the first occurrence of the element 

  🔹 ```if (x == arr[mid] && (mid == 0 || arr[mid-1] != x))```
- If element in left side but not mid or there are more occurrences of element to the left side of mid
    
  🔹 ```if (arr[mid] >= x) -> then search from 0 to mid-1```

### **Find Element in an infinite sorted array**
- Exponentially increase `i` till `arr[i]` become greater than target

- Now perform binary search between `i/2` and `i`

  🔹 ```return binarySearch(arr, x, i/2, i)```
