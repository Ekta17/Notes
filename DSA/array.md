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
    - reverse the whole array
    - Divide the array into two parts and reverse each part: 
    - `d %= nums.length` this is required to remove unnessary rotations when d > nums.length 
    - reverse the array from 0 to (d-1)
    - reverse the array from d to (n-1)
    

2. **Rotations to Left**: [1,2,3,4], d = 1 --> [2,3,4,1]
    - Reverse the whole array
    - Divide the array into two parts and reverse each part:
    - reverse the array from 0 to (d-1)
    - reverse the array from d to (n-1)
    
**Special condition:**

- Before performing any type of rotation, initialize **d %= array.length** to handle the case where length of array is less than d
- When d >= arr.length, d %= arr.length ensures you're not doing extra rotations — because rotating n times just brings the array back to where it started.
- **Example**: If the array has 5 elements and you want to rotate it 7 times to the left, rotating 7 times is the same as rotating 2 times (7 % 5 = 2), because after 5 rotations, the array comes back to its original position.
- **Why is it needed?**
    - Without this line, if you try to rotate the array more than its length (say, rotate a 5-element array by 7 positions), the code might:
        - do unnecessary work (inefficient), 
        - or even throw an error depending on how the logic is implemented.


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

### **Merge two sorted arrays**

- question: https://leetcode.com/explore/learn/card/fun-with-arrays/525/inserting-items-into-an-array/3253/
- **When arrays require inplace operation or moving the elements to the right, try to look for solutions
  where you can iterate the array from the end instead of starting.**
- In this question, its easy to compare elements from the end and instead of looking for smaller element
  we look for greater element and then insert it into the final array
- Time Complexity: O(n)
- Space Complexity: O(1)

**Code:** https://github.com/Ekta17/DataStructureAndAlgorithms/blob/main/src/main/java/arrays/MergeTwoSortedArray.java

### Inserting element at a given index (concept)

- Moving the elements to the right by one position can be done as following: Example we need to move the elements
  starting position 2 to 1 position to right to make space of new element in the array at position 2:

        // Say we want to insert the element at index 2.
        // First, we will have to create space for the new element.
        for (int i = intArray.length-1 ; i >= 2; i--){
            // Shift each element one position to the right.
            intArray[i + 1] = intArray[i];
        }
        // Now that we have created space for the new element,
        // we can insert it at the required index.
        intArray[2] = 30;


### Deleting an element at a given index (concept)

- Deleting the element from a given index which is not the last element in the array
  requires extra work. We need to move the elements from that index till the end of array 
  one position to the left. 

        // Say we want to delete the element at index 1
        for (int i = 2; i < length; i++) {
            // Shift each element one position to the left
            int_array[i - 1] = int_array[i];
        }

        // Again, the length needs to be consistent with the current
        // state of the array.
        length--; 


### In Place modification of Array (concept)

- Not using extra space to do the modification. 
  It is this technique of working directly in the input Array, 
  and not creating a new Array, that we call in-place. 
- In-place Array operations are a big deal for programming interviews, 
  where there is a big focus on minimising both time and space complexity of algorithms.
- If we create a new array instead of modifying the original array then that means that 
  other functions can no longer access the original data, 
  because it has been overwritten.

