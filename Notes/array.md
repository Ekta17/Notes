# Arrays

### **Reverse an array**

- Take two pointers
- Iterate one from beginning in the increasing order 
  and other from the end in decreasing order
- Swap the elements at the two pointer location till beginning pointer value 
  is less then end pointer value.
- Time Complexity: O(n)
- Space complexity: O(1)  
- **Note**: to compare two array values: **_assertArraysEquals(int[] expected, int[] actual)_**

**Code:** https://github.com/Ekta17/DataStructureAndAlgorithms/blob/main/src/main/java/arrays/ReverseArray.java


### **Rotate an array**

- Given an array and the '_d_' which is number of time the array needs to be rotated. 
- Using reversal of the array we can achieve this. 
- Divide the array into two parts: 
    - the array from 0-(d-1)
    - the array from d-(n-1)
- reverse both the arrays 
- now reverse the array which you got from the previous step. 
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
 
- question: https://leetcode.com/problems/best-time-to-buy-and-sell-stock/
- Time Complexity: O(n)
- Space Complexity: O(1)

**Code:** https://github.com/Ekta17/DataStructureAndAlgorithms/blob/main/src/main/java/arrays/BuyAndSellStock.java





