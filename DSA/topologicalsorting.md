#Topological Sort

**Directed Acyclic Graphs** 

A topological ordering of a directed graph is a way of ordering the list of nodes such that 
if (a,b) is an edge then 'a' will appear before 'b' in the ordered list. 

If a graph has cycles or is not directed, then there is no topological sort.

##### Applications:

- Graph representing part of the assembly line. Then topological sort would offer 
  a valid ordering for the assembly line.

##### Working:

- Take a stack 
- if a node is not visited
    - check if the node has children
    - if there are children
      - visit each child
      
- mark the node as visited
- add the node on top of the stack
- repeat this for all the nodes in the graph

##### Code:

https://github.com/Ekta17/DataStructureAndAlgorithms/blob/main/src/main/java/graph/sorting/TopologicalSort.java
