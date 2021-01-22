# LRUCache

We are given total possible page numbers that can be referred. 
We are also given cache (or memory) size (Number of page frames that cache can hold at a time). 
The LRU caching scheme is to remove the least recently used frame when the cache is full 
and a new page is referenced which is not there in cache.

##### Implementation:

- Using LinkedHashMap in java is the easiest way to implement a LRU cache as it maintains the 
order of insertion.
  
- So we can get constant time access, insertion and removal of elements from the cache

##### Working:

- We need a variable to keep track of the capacity of the cache. 
- We need a LinkedHashMap to hold the elements in the cache. 

**Get an element:** 
- If the cache does not contain the key return -1.
- If the cache contains the key:
  - get the value of the corresponding key
  - remove the element from the LinkedHashMap
  - put the (key,value) pair in the LinkedHashMap
- This removal and addition to the LinkedHashMap will ensure the least recently used element is always
stored as the first element in the map.
  
**Put an element:**
- if the element is present in the cache, remove the element 
- if the element is not present in the cache, remove the first element from the cache. 
    - First element of the LinkedHashMap is stored at **cache.keySet().iterator().next()** location.
- put the (key,value) pair in the LinkedHashMap


##### Code:

https://github.com/Ekta17/DataStructureAndAlgorithms/blob/main/src/main/java/random/LeastRecentlyUsedCache.java
