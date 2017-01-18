# About data structures learning.
- Note: 
  - Basic operations
  - Time Complexity
  - Use case

- Mainly used tutorials
  - Geekforgeeks : http://www.geeksforgeeks.org/data-structures/
  - TutorialPoint : https://www.tutorialspoint.com/data_structures_algorithms/index.htm

***

# Abstract Data Types (ADT)
Abstract data type describes what operations are available and what laws they obey.

- Array
  - Array is a container which can hold a fix number of items and these items should be of the same type.
  
- List
  - List is a linear data structure, which contains a sequence of elements.
  - The list allows adding elements on different positions, removing them and incremental crawling.
  
- Stack
  - The stack is a data structure, which implements the behavior "last in – first out" (LIFO).
  - the elements could be added and removed only on the top of the stack.
  - two principal operations: 
    - push, which adds an element to the collection.
    - pop, which removes the last element that was added.
  
- Queue
  - The abstract data structure "queue" satisfies the behavior "first in – first out" (FIFO).
  - Elements added to the queue are appended at the end of the queue, and when elements are extracted, they are taken from the beginning of the queue (in the order they were added).
  - two principal operations: 
    - enqueue, the process of adding an element to the collection.(The element is added from the rear side).
    - dequeue, the process of removing the first element that was added. (The element is removed from the front side).
  
- Set
  - set are unordered collections of unique elements.
  
- Priority Queue
  - it is like a regular queue or stack, but where additionally each element has a "priority" associated with it. 
  - In a priority queue, an element with high priority is served before an element with low priority. If two elements have the same priority, they are served according to their order in the queue.
  
- associative array (map, symbol table, or dictionary)
  - it is an abstract data type composed of a collection of (key, value) pairs, such that each possible key appears at most once in the collection.

# Linear Data Structures
A linear data structure traverses the data elements sequentially, in which only one data element can directly be reached.

## Array
Array is a data structure used to store homogeneous elements at contiguous locations. Size of an array must be provided before storing data.

## List
#### Array List

#### Linked List

Linked List is a sequence of links which contains items. Each link contains a connection to another link.

A linked list is a linear data structure (like arrays) where each element is a separate object. Each element (that is node) of a list is comprising of two items – the data and a reference to the next node.

- Simple/Singly Linked List : Item navigation is forward only.

- Doubly Linked List : Items can be navigated forward and backward.

- Circular Linked List : Last item contains link of the first element as next and the first element has a link to the last element as previous.
  
Advantages over arrays
- Dynamic size
- Ease of insertion/deletion

Drawbacks
- Random access is not allowed. We have to access elements sequentially starting from the first node. So we cannot do binary search with linked lists.
- Extra memory space for a pointer is required with each element of the list.

## Hash Table
Hash Table is a data structure which stores data in an associative manner. In a hash table, data is stored in an array format, where each data value has its own unique index value. Items are in the (key,value) format.

Hash Table uses an array as a storage medium and uses hash technique to generate an index where an element is to be inserted or is to be located from.

- Hashing : 
Hashing is a technique to convert a range of key values into a range of indexes of an array.

- Use case
  - Hashing can be used to remove duplicates from a set of elements. 
  - Can also be used find frequency of all items. For example, 
    - in web browsers, we can check visited urls using hashing. 
    - in firewalls, we can use hashing to detect spam. We need to hash IP addresses.     
  - Hashing can be used in any situation where want search() insert() and delete() in O(1) time.


# Non-linear Data Structures
Every data item is attached to several other data items in a way that is specific for reflecting relationships. The data items are not arranged in a sequential structure.

## Tree
Trees are hierarchical data structures.

#### Binary Tree

- A binary tree is a tree data structure in which each node has at most two children, which are referred to as the left child and the right child.

- A binary tree has the benefits of both an ordered array and a linked list as search is as quick as in a sorted array and insertion or deletion operation are as fast as in linked list.

- A Binary Tree node contains following parts.
  - Data
  - Pointer to left child
  - Pointer to right child
    
- A Binary Tree can be traversed in two ways:
  - Depth First Traversal: 
    - Inorder (Left-Root-Right).
    - Preorder (Root-Left-Right).
    - Postoder (Left-Right-Root).
    
  - Breadth First Traversal: Level Order Traversal
  
- Use case
  - One reason to use binary tree or tree in general is for the things that form a hierarchy, eg:
    - File structures
    - JavaScript DOM

#### Binary Search Tree (BST)

- Binary Search Tree is a Binary Tree with following additional properties:
  - The left subtree of a node contains only nodes with keys less than the node’s key.
  - The right subtree of a node contains only nodes with keys greater than the node’s key.
  - The left and right subtree each must also be a binary search tree.
  
- Time Complexities:  
  - BST provide moderate access/search (quicker than Linked List and slower than arrays).
  - BST provide moderate insertion/deletion (quicker than Arrays and slower than Linked Lists).
  
- Use case
  - Its main use is in search application where data is constantly entering/leaving and data needs to printed in sorted order. eg:
    - E- commerce websites, where a new product is added or product goes out of stock and all products are lised in sorted order. 

#### Binary Heap

- A Binary Heap is a Binary Tree with following properties:
  - It’s a complete tree (All levels are completely filled except possibly the last level and the last level has all keys as left as possible). This property of Binary Heap makes them suitable to be stored in an array.
  - A Binary Heap is either Min Heap or Max Heap. In a Min Binary Heap, the key at root must be minimum among all keys present in Binary Heap. The same property must be recursively true for all nodes in Binary Tree. Max Binary Heap is similar to Min Heap. It is mainly implemented using array.
  
- Use case
  - Used in implementing efficient priority-queues, which in turn are used for scheduling processes in operating systems. Priority Queues are also used in Dijstra’s and Prim’s graph algorithms.
  - Order statistics: The Heap data structure can be used to efficiently find the k’th smallest (or largest) element in an array.
  - Heap is a special data structure and it cannot be used for searching of a particular element.


## Graph
A graph is a pictorial representation of a set of objects where some pairs of objects are connected by links. The interconnected objects are represented by points termed as vertices, and the links that connect the vertices are called edges.

A graph is a pair of sets (V, E), where V is the set of vertices and E is the set of edges, connecting the pairs of vertices.

Terms:
- Vertex − Each node of the graph is represented as a vertex.
- Edge − Edge represents a path between two vertices or a line between two vertices.
- Adjacency − Two node or vertices are adjacent if they are connected to each other through an edge.
- Path − Path represents a sequence of edges between the two vertices.

Use case:
- The most common example of the graph is to find shortest path in any network. Used in google maps or bing. 
- Another common use application of graph are social networking websites where the friend suggestion depends on number of intermediate suggestions and other things.

Graph Traversal
- Depth First Search (DFS) : traverses a graph in a depthward motion and uses a stack to remember to get the next vertex to start a search, when a dead end occurs in any iteration.

  - It employs the following rules:
    - Rule 1 : Visit the adjacent unvisited vertex. Mark it as visited. Display it. Push it in a stack.
    - Rule 2 : If no adjacent vertex is found, pop up a vertex from the stack. (It will pop up all the vertices from the stack, which do not have adjacent vertices.)
    - Rule 3 : Repeat Rule 1 and Rule 2 until the stack is empty.
  
- Breadth First Search (BFS) : traverses a graph in a breadthward motion and uses a queue to remember to get the next vertex to start a search, when a dead end occurs in any iteration.  
  - It employs the following rules:
    - Rule 1 − Visit the adjacent unvisited vertex. Mark it as visited. Display it. Insert it in a queue.
    - Rule 2 − If no adjacent vertex is found, remove the first vertex from the queue.
    - Rule 3 − Repeat Rule 1 and Rule 2 until the queue is empty.
    
***

# Advanced Data structures
TBD...

***

# Reference
- List of data structures
  - https://en.wikipedia.org/wiki/List_of_data_structures#Lists
 
- Overview of Data Structures | Set 1 (Linear Data Structures)
  - http://www.geeksforgeeks.org/overview-of-data-structures-set-1-linear-data-structures/
  
- Overview of Data Structures | Set 2 (Binary Tree, BST, Heap and Hash)
  - http://www.geeksforgeeks.org/overview-of-data-structures-set-2-binary-tree-bst-heap-and-hash/
  
- Overview of Data Structures | Set 3 (Graph, Trie, Segment Tree and Suffix Tree)
  - http://www.geeksforgeeks.org/overview-of-data-structures-set-3-graph-trie-segment-tree-and-suffix-tree/

- Linear Data Structures
  - http://www.introprogramming.info/english-intro-csharp-book/read-online/chapter-16-linear-data-structures/

- Abstract data structure set
  - http://www.introprogramming.info/english-intro-csharp-book/read-online/chapter-18-dictionaries-hash-tables-and-sets/#_Toc362296548
  
- What are the differences between Map, Hash and Dictionary in programming languages?
  - https://www.quora.com/What-are-the-differences-between-Map-Hash-and-Dictionary-in-programming-languages

- Associative array
  - https://en.wikipedia.org/wiki/Associative_array
  
- Priority queue
  - https://en.wikipedia.org/wiki/Priority_queue
  
- Tree Traversal
  - https://www.tutorialspoint.com/data_structures_algorithms/tree_traversal.htm

- Graph Theory Tutorial
  - https://www.tutorialspoint.com/graph_theory/index.htm
