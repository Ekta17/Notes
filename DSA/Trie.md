# Trie Tree

Trie tree is used for quick retrieval of words from a dictionary.

##### Implementation:

- Root node doesnt contain any character. It has children array of size alphabets. 
- Each node has an array of alphabets.
- There exist a boolean variable which keeps track of end of the word. 
  
- **Time complexity = O(M)** 
  where M is the size of the word to search.
  This is same to find a word as well as to insert a new word,
- **Space complexity = O(ALPHABET_SIZE * M * N)**, 
  where M is the average word length, 
        N is the number of words

##### Working:

- Create a root node and initialize its children with new array of size ALPHABET
and mark its endOfWord = false in the constructor. 

**Insert a new word:** 
- Create a current node which point to root of the trie. 
- Iterate through each character in the trie 
  and check if the index position character - alphabet 'a' is null or not.
- if the index position is null then create a new node at index = character - alphabet 'a'
- move to the next character making the current node = current.children[c -'a'], 
  i.e. move current node to the index of the character - alphabet 'a'. 
  
**Search a word:**
- Create a current node which point to root of the trie.
- Iterate through each character in the trie
  and check if the index position character - alphabet 'a' is null or not.
- if the index position is null then return false meaning the word doesn't exist
- else keep iterating 
- At the end of the iteration current will point to the last node of the word
- check if this node is the end of the word --> isEndOfWord = true.
- if its end of the word, return true 
- else return false

**Search a Prefix:**
- It is same as searching for the word with only difference being 
  we do not have to check the end of word at the end of iteration 
  as this is a prefix search. 

##### Code:

https://github.com/Ekta17/DataStructureAndAlgorithms/blob/main/src/main/java/trees/trie/TrieTree.java
