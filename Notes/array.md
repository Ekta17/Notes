# Arrays

### **Reverse an array**

- Take two pointers
- Iterate one from beginning in the increasing order 
  and other from the end in decreasing order
- Swap the elements at the two pointer location till beginning pointer value 
  is less then end pointer value.
- Time Complexity: O(n)
- Space complexity: O(1)  
- **Note**: to compare two array values: **_assertArrayEquals(int[] expected, int[] actual)_**

**Code:** https://github.com/Ekta17/DataStructureAndAlgorithms/blob/main/src/main/java/arrays/ReverseArray.java


### **Rotate an array**

- Given an array and the '_d_' which is number of time the array needs to be rotated. 
- Using reversal of the array we can achieve this. 

1. **Rotations to Right**: [1,2,3,4], d = 1 --> [4,1,2,3]
    - Divide the array into two parts and reverse each part: 
    - reverse the array from 0 to (d-1)
    - reverse the array from d to (n-1)
    - now reverse the whole array

2. **Rotations to Left**: [1,2,3,4], d = 1 --> [2,3,4,1]
    - Reverse the whole array
    - Divide the array into two parts and reverse each part:
    - reverse the array from 0 to (d-1)
    - reverse the array from d to (n-1)
    
Note: Before performing any type of rotation, initialize **d %= array.length** 
        to handle the case where length of array is less than d    

- Time Complexity: O(n)
- Space Complexity: O(1)

**Code:** https://github.com/Ekta17/DataStructureAndAlgorithms/blob/main/src/main/java/arrays/RotateArray.java


### **Leaders in an array**

- Leader in an array is the elements whose all the elements on the right are smaller. 
- example - {5,3,20,15,8,3} --> leaders[] = {20, 15, 8, 3}
- start with the end of the array, mark it as max and add it into the list of leaders
- now iterate from end to beginning of the array and keep comparing with current max. 
- if the element is greater than max add to leaders list and mark it as max.
- Time Complexity: O(n)
- Space Complexity: O(1)

**Code:** https://github.com/Ekta17/DataStructureAndAlgorithms/blob/main/src/main/java/arrays/LeadersInArray.java


### **Best time to buy and sell stock**
 
1) https://leetcode.com/problems/best-time-to-buy-and-sell-stock/
   - You want to maximize your profit by choosing a single day to buy one stock 
     and choosing a different day in the future to sell that stock. 
   - Return the maximum profit you can achieve from this transaction. 
     If you cannot achieve any profit, return 0.
   - Since you can buy on one day and sell on another day, 
     i.e. only one transaction is allowed. create a variable to set buyPrice
   - If current element's value is less than buyPrice, update buyPrice as current Price. 
   - else calculate current Profit --> currentPrice[i] - buyPrice, and then update 
      max profit by comparing current value of maxProfit with currentProfit.

2) https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/
    - In this question, we need to find maxProfit no matter how many times we do the 
      transaction i.e. buy and sell any number of times.
    - Here we need to find localMinima and localMaxima.
    - set localMinimaIndex = 0
    - iterate through the price array starting from position 1
      - if current price is less than previous element's price, then update localMinimaIndex as current index. 
      - find localMaxima such that --> previous element <= current Element > next element. 
      - if you find localMaxima, add to maxProfit.
  
- Time Complexity: O(n)
- Space Complexity: O(1)

**Code:** https://github.com/Ekta17/DataStructureAndAlgorithms/blob/main/src/main/java/arrays/BuyAndSellStock.java

### **Remove duplicates from sorted array**

- question: https://leetcode.com/explore/featured/card/top-interview-questions-easy/92/array/727/
- Time Complexity: O(n)
- Space Complexity: O(1)

**Code:** https://github.com/Ekta17/DataStructureAndAlgorithms/blob/main/src/main/java/arrays/RemoveDuplicatesFromSortedArray.java


### **PrefixSum Technique**

- Given an array arr[] of size n, its prefix sum array is another array prefixSum[]
  of same size such that the value of prefixSum[i] is arr[0] + arr[1] + arr[2] … arr[i]
- Example: 
    - Input  : arr[] = {10, 20, 10, 5, 15}
    - Output : prefixSum[] = {10, 30, 40, 45, 60}
    - Explanation : While traversing the array, update 
      the element by adding it with its previous element.
        prefixSum[0] = 10,
        prefixSum[1] = prefixSum[0] + arr[1] = 30,
        prefixSum[2] = prefixSum[1] + arr[2] = 40 and so on.
- https://www.geeksforgeeks.org/prefix-sum-array-implementation-applications-competitive-programming/?ref=leftbar-rightbar







