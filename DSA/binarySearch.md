# Binary Search

### **Searching in sorted array**

- Divide the array into 2 parts, where the elements on left side of the mid is less in value that mid and elements on right side of mid are greater in value
- Can be solved iteratively or recursively
- Find mid: to avoid overflow of int values when large arrays are involved, the optimal way to find mid is **low + (high-low)/2** 
- Time Complexity: O(log n)
- **Note**: base case for recurrsion is when ```low > high``` then return false

**Code:** https://github.com/Ekta17/DSA/blob/main/src/main/dsa/search/BinarySearch.java

### **Finding first occurrence of an element in sorted array**

- Check if mid is the element, then find if mid is the first occurrence of the element, then return mid
    ```
        if(x == arr[mid] && (mid == 0 || arr[mid-1] != x))
            return mid;
    ```
- Check if mid if not the first occurrence or mid is not element and element is less then mid, then search left of mid
    ```
        else if (arr[mid] >= x)
            return binarySearch(arr, x, low, mid-1);
    ```
- Else search right side of mid
  ```
        return binarySearch(arr, x, mid+1, high);
    ```
- **Note**: base case remains same is when ```low > high``` then return -1

**Code:** https://github.com/Ekta17/DSA/blob/main/src/main/dsa/search/FirstOccurrenceOfElementSortedArray.java


### **Find Element in an infinite sorted array**

- Check if 1st element is the target, then return 0
    
- Now initialize a variable `i`, such that till we find `arr[i]` that is greater than target, we keep incrementing i exponentially
    ```
        i = 1
        while (arr[i] < x)
          i = i * 2; 
    ```
- After the loop breaks, check if `arr[i]` is target, then return `i`
  
- or else, target lies between `i/2` and `i`, so do a binary search between those indexes
  ```
        return binarySearch(arr, x, i/2, i);
    ```
  
- **Note**: why binary search `i/2` and `i`, because if target is less than `i/2`, we would have broke the loop before that

**Code:** https://github.com/Ekta17/DSA/blob/main/src/main/dsa/search/SearchTargetInfinitArray.java
