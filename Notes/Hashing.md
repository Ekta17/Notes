# Hashing

- Search, Insert, Delete operations in O(1) time

- In Java: 
    - **Set Interface**: contains Unique elements. If a duplicate element is tried to insert, does not add it.  
        - HashSet
        - LinkedHashSet: Maintains order of insertion 
    - **Map Interface**: Stores (key,value) pairs
        - HashMap
        - LinkedHashMap: maintains order of insertion
    - **Operations**:
        - add(key) / put(key,value)
        - remove(key)
        - size() 
        - contains(key) / containsKey(key) / containsValue(value)

- **Self balancing**: 
    - Search, Insert, Delete - O(log n) time
    - Maintains sorted order of keys 
    - Set: 
        - TreeSet
    - Map: 
        - TreeMap
    
- If input is of finite small size, we can use an array instead of hashset/hashmap:
    
        //sample array containing 26 elements
        boolean set[26] =  {false, false, ..., false}
        set[i-'a'] = true;   

### Simple implementation of  Hash function:

    - bucket = input_size % prime_number
    - number of buckets = 0 to (prime_number-1)
    - each element in the bucket is stored as LinkedList or Self balancing tree

### Key Collision:

- When two or more keys are part of the same bucket i.e. the return of hash function is equal.
    Two ways to handle collisions: 
    - **Linear chaining**: 
        - number of buckets = prime_number
        - keys with same hash are stored as LinkedList or Self balancing tree
        - by using self balancing tree we reduce the time of searching a key from O(n) to O(log n)
        - Not cache friendly
        - Not sensitive to hash function
    - **Open Addressing:**
        - number of buckets = size of input
        - If a key has the hash number which is already occupied by another key then, we search the next avialable spot
    by the method of linear probing i.e. linear searching for next available spot and insert the key there.
        - There are two types of probing techniques: 
            - **Linear probing** 
            - **Quadratic probing**
        - Now when we need to delete a key, we do not simply remove the key, but 
      mark it with special value which helps maintain searching operation.
        - cache friendly technique  
        - sensitive to hash function

### Questions:

- Find a subarray with zero sum
  
    **Code:** https://github.com/Ekta17/DataStructureAndAlgorithms/blob/main/src/main/java/arrays/prefixsum/ZeroSumSubarray.java
      
- Find a subarray with given sum 
    
    **Code:** https://github.com/Ekta17/DataStructureAndAlgorithms/blob/main/src/main/java/arrays/prefixsum/GivenSumSubarray.java
  