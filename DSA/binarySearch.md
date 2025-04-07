# Binary Search

### **Searching in sorted array**

- Divide the array into 2 parts, where the elements on left side of the mid is less in value that mid and elements on right side of mid are greater in value
- Can be solved iteratively or recursively
- Find mid: to avoid overflow of int values when large arrays are involved, the optimal way to find mid is **low + (high-low)/2** 
- Time Complexity: O(log n)
- **Note**: base case for recursion is when ```low > high``` then return false

**Code:** https://github.com/Ekta17/DSA/blob/main/src/main/dsa/search/BinarySearch.java
