# Heaps 

Complete Binary tree (totally filled other than rightmost element at the last level). 

**Parent index:** i

**LeftChild index:** 2*i + 1

**RightChild index:** 2*i + 2

for any node i, its parent is at floor((i-1)/2)


**Max Heap:** Root is the max element

**Min Heap:** Root is the min element

We use array as the internal data structure to implement heaps as it provides cache friendliness. 

### Implementation of Heap data structure

**Priority queues**
**Used in the following algorithms:**
    
    - Dijkstra's Algorithm
    - Prim's Algorithm
    - Huffman code Algorithm
    - Scheduling jobs in the processor

### Operations on Heap 

**Build a Heap** from the given array: Time complexity is **O(n)** 

    - start from the last Parent in the subtree and build it to root element of the tree
    - Index position of the last Parent element is at (n-2)/2, 
        this is derived as the last element is at n-1 location, 
        where n is the size of the array. Since Heap is a complete binary tree, 
        the leftchild must exist. Hence, if the parent is at i, the left child is at 
        (2*i+1) index i.e. (n-1) = 2*i +1 --> i = (n-2)/2
    - Start a loop from (n-2)/2 to 0 and call heapify function at each step to maintain heap property at every subtree level.
    

**Insert** a new element into the heap: Time complexity is **O(log n)**

    - Insert the new element at the last leaf location i.e. at the end of the array 
    - Then perform heapify from the last subtree to root of the tree to find the correct location of new element/

**Extract Min/Max** element from the heap: Time complexity is **O(log n)**

    - Swap last element and the root element of the tree i.e. arr[0] and arr[n-1]
    - Perform heapify from root to boot leaf node to maintian heap property 

**Heapify** algorithm used to maintain min/max heap property: Time complexity is **O(log n)**

    - for a subtree, compare Parent, leftchild and rightchild, and get the smallest element 
        for min heap and largest element in case of Max heap. 
    - swap this smallest element with the Parent element, if the index of parent element is not same as 
        smallest element, i.e. Parent is not the smallest element in the current tree. 
    - call heapify to maintain heap property on the smallest element index. 

**Delete** element from the heap: Time complexity is **O(log n)**

    - to delete an element from the heap, swap the element with last element from the heap stored at n-1 location.
    - decrease the size of the heap by 1 to remove the last element. 
    - now perform heapify from this element's index subtree to all the up to the root of the tree, 



All the operations other than building the heap take O(log n) time which is same time taken by self balancing trees like 
Red-Black tree, AVL tree, but one of the key difference is to build the heap it takes O(n) time 
where as to build a self balancing tree, it take O(nlog n) time. And also, its easier to work with arrays.

### Java implementation of Heap

PriorityQueue<T> 

**Min Heap:** PriorityQueue<T> pq = new PriorityQueue<>(); 

**Max Heap:** PriorityQueue<Integer> pq = new PriorityQueue<>(**Collections.reverseOrder()**);