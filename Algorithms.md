# Algorithms  
  
## Dynamic connectivity  
  
###### Given a set of N objects  
* Union command: connect two objects  
* Find/connected query: is there a path connecting the two objects?  

---

###### Applications  
* Pixels in a digital photo.  
* Computers in a network.  
* Friends in a social network.  
* Transistors in a computer chip.  
* Elements in a mathematical set.  
* Variable names in Fortran program.  
* Metallic sites in a composite system.  

---

###### It is assumed that "is connected to" is an equivalence relation:  
* Reflexive: p is connected to p.  
* Symmetric: if p is connected to q, then q is connected to p.  
* Transitive: if p is connected to q and q is connected to r, then p is connected to r.  

---

| Algorithm  | Initialize  | Union  | Connected  | Note  |
| ---------- |:-----------:|:------:|:----------:|:-----:|
| Quick-Find  | N | N | 1 |  Eager approach|
| Quick-Union  | N | N | N ||
| Weighted Quick-Union  | N | lg N | lg N ||

##Contiguous vs. Linked Data Structures  
Data structures can be neatly classified as either contiguous or linked, depending upon whether they are based on arrays or pointers:  
* __Contiguously-allocated structures__ are composed of single slabs of memory, and include arrays, matrices, heaps, and hash tables.  
* __Linked data structures__ are composed of distinct chunks of memory bound together by pointers, and include lists, trees, and graph adjacency lists.  
 
##Contiguous (Arrays)  
The array is the fundamental contiguously-allocated data structure. Arrays are structures of fixed-size data records such that each element can be efficiently located by its index or (equivalently) address.  
__Advantages of contiguously-allocated arrays include:__
* Constant-time access given the index – Because the index of each element maps directly to a particular memory address, we can access arbitrary data items instantly provided we know the index.  
* Space efficiency – Arrays consist purely of data, so no space is wasted with links or other formatting information. Further, end-of-record information is not needed because arrays are built from fixed-size records.  
* Memory locality – A common programming idiom involves iterating through all the elements of a data structure. Arrays are good for this because they exhibit excellent memory locality. Physical continuity between successive data accesses helps exploit the high-speed cache memory on modern computer architectures.  

__Disadvantage of contiguously-allocated arrays include:__  
* Cannot adjust their size in the middle of a program’s execution. Our program will fail soon as we try to add the (n + 1)st customer, if we only allocate room for n records. We can compensate by allocating extremely large arrays, but this can waste space, again restricting what our programs can do.  

##Linked Data Structures (Linked List)  
* Overflow on linked structures can never occur unless the memory is actually full.  
* Insertions and deletions are simpler than for contiguous (array) lists.  
* With large records, moving pointers is easier and faster than moving the items themselves.  

Relative advantages of arrays include:  
* Linked structures require extra space for storing pointer fields.  
* Linked lists do not allow efficient random access to items.  
* Arrays allow better memory locality and cache performance than random pointer jumping.  

Recursive View  
* Lists – Chopping the first element off a linked list leaves a smaller linked list. This same argument works for strings, since removing characters from string leaves a string. Lists are recursive objects.  
* Arrays – Splitting the first k elements off of an n element array gives two smaller arrays, of size k and n-k, respectively. Arrays are recursive objects.  

---

##Stacks
Support retrieval by last-in, first-out (LIFO) order. Stacks are simple to implement and very efficient. For this reason, stacks are probably the right container to use when retrieval order doesn’t matter at all, such as when processing batch jobs. The put and get operations for stacks are usually called push and pop:
* __Push(x,s):__ Insert item x at the top of stack s.  
* __Pop(s):__ Return (and remove) the top item of stack s.  

##Dynamic Arrays (Resizing Array)
Support the ability to resize an array dynamically (when needed).  
* __Grow Array:__ If array is full, create a new array of twice the size, and copy items (repeated doubling). Cost of inserting first N items. N + (2 + 4 + 8 + … + N) ~ 3N.  
* __Shrink Array:__  Halve size of array when array is one-quarter full (1/4). If we halve size of array when array is one-half full thrashing could happen by adding and removing if the array is full.  

##Queues
Support retrieval in first in, first out (FIFO) order. This is surely the fairest way to control waiting times for services. You want the container holding jobs to be processed in FIFO order to minimize the maximum time spent waiting. Note that the average waiting time will be the same regardless of whether FIFO or LIFO is used. Many computing applications involve data items with infinite patience, which renders the question of maximum waiting time moot.  
* __Enqueue(x,q):__ Insert item x at the back of queue q.  
* __Dequeue(q):__ Return (and remove) the front item from queue q.  

##Dictionaries
The dictionary data type permits access to data items by content. You stick an item into a dictionary so you can find it when you need it.  

##Trees  
  
##Properties of binary trees
* The number of nodes n in a full binary tree, is at least n = 2^h and at most n = 2^(h+1) - 1, where h is the height of the tree. A tree consisting of only a root node has a height of 0.  
* The number of leaf nodes l in a perfect binary tree, is l = (n + 1) / 2. (to find the value of n look above point)  
* In a perfect full binary tree, l = 2^(h) thus n = 2^(h+1) - 1.  

##Heaps (Priority Queues) 
* __Heapify :__ which runs in O(lg n) time.
* __Build-Heap :__ which runs in linear time.
* __Heap Sort :__ which runs in O(n lg n) time.
* __Extract-Max :__ which runs in O(lg n) time.

>  In array implementation if array index starts with Zero then  
>  iParent      = floor((i-1) / 2)  
>  iLeftChild  = 2*i + 1  
>  iRightChild = 2*i + 2  
>  
>  if index start with 1  
>  iParent      = floor((i) / 2)  
>  iLeftChild   = 2*i  
>  iRightChild = 2*i + 1  

A heap is a specialized tree-based data structure that satisfies the heap property: If A is a parent node of B then the key of node A is ordered with respect to the key of node B with the same ordering applying across the heap. Either the keys of parent nodes are always greater than or equal to those of the children and the highest key is in the root node (this kind of heap is called max heap) or the keys of parent nodes are less than or equal to those of the children and the lowest key is in the root node (min heap).  
Heaps has the following properties:
* All levels except last level are full. Last level is left filled.
* Priority of a node is at-least as large as that of its parent (min-heap) (or) vice-versa (max-heap).
* If the smallest element is in the root node, it results in a min-heap.
* If the largest element is in the root node, it results in a max-heap.
* A heap can be thought of as a priority queue. The most important node will always be at the root of the tree.
* Heaps can also be used to sort data, heap sort.
* The two most interesting operations in a heap is heapifyup and heapifydown.  

Assumption min-heap  
__Heapify-up__ (swim)  
Used to add a node to the heap. To add a node, it is inserted at the last empty space and heapify-up process is done. When a node is added, its key is compared to its parent. If parent key is smaller than the current node it is swapped. The process is repeated till the heap property is met.  

__Heapify-down__ (sink)  
Used during removal of a node. When a node is removed which is always the root (lowest in priority) the last available node in heap is replaced as the root and heapify-down process is done. The key of parent node is compared with the children. If any of the children have lower priority it is swapped with the parent. The process is repeated for the newly swapped node till the heap property is met.  

##Binary Search Trees 
[Wikipedia Tree traversal](https://en.wikipedia.org/wiki/Tree_traversal)  
The binary search tree labeling uniquely identities where each key is located. Start at the root. Unless it contains the query key x, proceed either left or right depending upon whether x occurs before or after the root key.  
__Traversal in a Tree__  
###Depth First
There are three types of __depth-first__ traversal: __pre-order__, __in-order__, and __post-order__  
* __Pre-order__  
Display the data part of root element (or current element).  
Traverse the left subtree by recursively calling the pre-order function.  
Traverse the right subtree by recursively calling the pre-order function.  
  
__Uses of Preorder__  
Preorder traversal is used to create a copy of the tree.  
Preorder traversal is also used to get prefix expression on of an expression tree.  
[Wikipedia Polish Notation](http://en.wikipedia.org/wiki/Polish_notation)  
![Preorder](https://github.com/amroibrahim/Notes/blob/master/Images/Algorithms/Sorted_binary_tree_preorder.png)  
Pre-order: F, B, A, D, C, E, G, I, H    
  
* __In-order__  
Traverse the left subtree by recursively calling the in-order function.  
Display the data part of root element (or current element).  
Traverse the right subtree by recursively calling the in-order function.  

__Uses of Inorder__  
In case of binary search trees (BST), Inorder traversal gives nodes in non-decreasing order. To get nodes of BST in non-increasing order, a variation of Inorder traversal where Inorder itraversal s reversed, can be used.  
![Inorder](https://github.com/amroibrahim/Notes/blob/master/Images/Algorithms/Sorted_binary_tree_inorder.png)  
 In-order: A, B, C, D, E, F, G, H, I  
  
* __Postorder__  
Traverse the left subtree by recursively calling the post-order function.  
Traverse the right subtree by recursively calling the post-order function.  
Display the data part of root element (or current element).  
  
__Uses of Postorder__  
Postorder traversal is used to delete the tree. Please see the question for deletion of tree for details. Postorder traversal is also useful to get the postfix expression of an expression tree.  
[Wikipedia Reverse Polish Notation](http://en.wikipedia.org/wiki/Reverse_Polish_notation)  
![Postorder](https://github.com/amroibrahim/Notes/blob/master/Images/Algorithms/Sorted_binary_tree_postorder.png)  
Post-order: A, C, E, D, B, H, I, G, F  

###Breadth-first search (Level-order)  
The algorithm uses a queue data structure to store intermediate results as it traverses the graph, as follows:  
1.  Enqueue the root node  
2.  Dequeue a node and examine it, If the element sought is found in this node, quit the search and return a result. Otherwise enqueue any successors (the direct child nodes) that have not yet been discovered.  
3.  If the queue is empty, every node on the graph has been examined – quit the search and return "not found".  
4.  If the queue is not empty, repeat from Step 2  
![Breadth](https://github.com/amroibrahim/Notes/blob/master/Images/Algorithms/Sorted_binary_tree_breadth-first_traversal.png)  

##Balanced Search Trees  
###2-3 Search Trees  
[Wikipedia 2–3 tree](https://en.wikipedia.org/wiki/2%E2%80%933_tree)  
A 2–3 tree is a tree data structure, where every node with children (internal node) has either two children (2-node) and one data element or three children (3-nodes) and two data elements.  
* Symmetric order: Inorder traversal yields keys in ascending order.  
* Perfect balance: Every path from root to null link has same length.  

__Search__  
1.  Compare search key against keys in node.  
2.  Find interval containing search key.  
3.  Follow associated link (recursively).  

__Insertion into a 3-node at bottom__  
1.  Add new key to 3-node to create temporary 4-node.  
2.  Move middle key in 4-node into parent.  
3.  Repeat up the tree, as necessary.  
4.  If you reach the root and it's a 4-node, split it into three 2-nodes.  

__AVL VS Red-Black__  
The AVL trees are more balanced compared to Red Black Trees, but they may cause more rotations during insertion and deletion. So if your application involves many frequent insertions and deletions, then Red Black trees should be preferred. And if the insertions and deletions are less frequent and search is more frequent operation, then AVL tree should be preferred over Red Black Tree.

###Left-Leaning Red-Black Balanced Search Trees  
[Wikipedia Red-Black tree](https://en.wikipedia.org/wiki/Red%E2%80%93black_tree)  
__Red-Black Tree__ Represents 2-3 trees as BST. It uses "internal" links as an indication of 3 nodes ( red link means they are in same node)
  
__Properties of Red Black Trees__  
1.  A node is either red or black.  
2.  The root is black. This rule is sometimes omitted. Since the root can always be changed from red to black, but not necessarily vice versa, this rule has little effect on analysis.  
3.  All leaves are black.  
4.  If a node is red, then both its children are black.  
5.  Every path from a given node to any of its descendant NULL nodes contains the same number of black nodes. Some definitions: the number of black nodes from the root to a node is the node's black depth; the uniform number of black nodes in all paths from root to the leaves is called the black-height of the red–black tree.  

__Elementary Operations__  

__1.  Left rotation__  
  
Before  
![Left Rotation Before](https://github.com/amroibrahim/Notes/blob/master/Images/Algorithms/Left_rotation_before.png)  

After  
![Left Rotation After](https://github.com/amroibrahim/Notes/blob/master/Images/Algorithms/Left_rotation_after.png)  

__2.  Right rotation__  
  
Before  
![Right Rotation Before](https://github.com/amroibrahim/Notes/blob/master/Images/Algorithms/Left_rotation_after.png)  

After  
![Right Rotation After](https://github.com/amroibrahim/Notes/blob/master/Images/Algorithms/Left_rotation_before.png)  
  
__3.  Color flip__  
  
Before  
![Color flip Before](https://github.com/amroibrahim/Notes/blob/master/Images/Algorithms/Color_flip_before.png)  

After  
![Color flip After](https://github.com/amroibrahim/Notes/blob/master/Images/Algorithms/Color_flip_after.png)  


__Insertion__  
*  Simple case  
If the new node is root, change color of new node to BLACK  
  
*  Other Cases  
Do standard BST insert; color new link red  
now check parent node  
 1.  is right child red and left child is black -> rotate left  
 2.  is left child red and left left child is red -> rotate right  
 3.  is left child red and right child red -> flip colors  
 4.  Now check if parent(s) has all those cases true  

###B-Trees  
B-Tree is a self-balancing search tree. It is an extention of binary search tree, but insted of having 2 childrin each node has at most M children.  

__Properties of B-Trees__  
[Wikipedia B-tree](https://en.wikipedia.org/wiki/B-tree)  
B-tree is a self-balancing tree data structure that keeps data sorted and allows searches, sequential access, insertions, and deletions in logarithmic time. The B-tree is a generalization of a binary search tree in that a node can have more than two children.  
 1.  Every node has at most m children.
 2.  Every non-leaf node (except root) has at least ⌈m/2⌉ children.
 3.  The root has at least two children if it is not a leaf node.
 4.  A non-leaf node with k children contains k−1 keys.
 5.  All leaves appear in the same level

###AVL Trees  
[Wikipedia AVL tree](https://en.wikipedia.org/wiki/AVL_tree)  
AVL tree is a self-balancing binary search tree. It was the first such data structure to be invented.[2] In an AVL tree, the heights of the two child subtrees of any node differ by at most one; if at any time they differ by more than one, rebalancing is done to restore this property. Lookup, insertion, and deletion all take O(log n) time in both the average and worst cases, where n is the number of nodes in the tree prior to the operation. Insertions and deletions may require the tree to be rebalanced by one or more tree rotations.  
  
###k-d Trees  
[Wikipedia k-d tree](https://en.wikipedia.org/wiki/K-d_tree)  
k-d trees is a space-partitioning data structure for organizing points in a k-dimensional space. k-d trees are a useful data structure for several applications, such as searches involving a multidimensional search key (e.g. range searches and nearest neighbor searches). k-d trees are a special case of binary space partitioning trees.  
  
###Interval Search Trees  
[Wikipedia Interval tree](https://en.wikipedia.org/wiki/Interval_tree)  
Interval tree is a tree data structure to hold intervals. Specifically, it allows one to efficiently find all intervals that overlap with any given interval or point. It is often used for windowing queries, for instance, to find all roads on a computerized map inside a rectangular viewport, or to find all visible elements inside a three-dimensional scene. A similar data structure is the segment tree.  
  
##Graphs  
[Wikipedia Graph](https://en.wikipedia.org/wiki/Graph_(abstract_data_type))
  
###Graph Anatomy  
![Graph Anatomy](https://github.com/amroibrahim/Notes/blob/master/Images/Algorithms/Graph_anatomy.png)  
  
###Representations  
__Adjacency matrix__  
A two-dimensional matrix, in which the rows represent source vertices and columns represent destination vertices. Data on edges and vertices must be stored externally. Only the cost for one edge can be stored between each pair of vertices.  
  
__Adjacency list__  
Vertices are stored as records or objects, and every vertex stores a list of adjacent vertices. This data structure allows the storage of additional data on the vertices. Additional data can be stored if edges are also stored as objects, in which case each vertex stores its incident edges and each edge stores its incident vertices.  
  
__Incidence matrix__  
A two-dimensional Boolean matrix, in which the rows represent the vertices and columns represent the edges. The entries indicate whether the vertex at a row is incident to the edge at a column.  
  
__Incidence list__  
 A collection of unordered lists used to represent a finite graph. Each list describes the set of neighbors of a vertex in the graph. This is one of several commonly used representations of graphs for use in computer programs.  

| Node / Edge Managment | Storage    | Add Vertex | Add Edge   | Remove Vertex | Remove Edge | Query  | Notes                       |
| --------------------- |:-----------|:-----------|:-----------|:--------------|:------------|:-------|:----------------------------|
| Adjacency Matrix      | O(V^2)     | O(V^2)     | O(1)       | O(V^2)        | O(1)        | O(1)   | Slow to add or remove vertices, because matrix must be resized/copied |
| Adjacency List        | O(V+E)     | O(1)       | O(1)       | O(E)          | O(E)        | O(V)   |	Slow to remove vertices and edges, because it needs to find all vertices or edges|
| Incidence Matrix      | O(V*E)     | O(V*E)     | O(V*E)     | O(V*E)        | O(V*E)      | O(E)   | Slow to add or remove vertices and edges, because matrix must be resized/copied |
| Incidence List        | O(V+E)     | O(1)       | O(1)       | O(E)          | O(E)        | O(E)   |   |
  
  
 __Undirected vs. Directed__  
 A graph G = (V,E) is undirected if edge (x, y) ? E implies that (y, x) is also in E. If not, we say that the graph is directed. Road networks between cities are typically undirected, since any large road has lanes going in both directions. Street networks within cities are almost always directed, because there are at least a few one-way streets lurking somewhere. Program-flow graphs are typically directed, because the execution flows from one line into the next and changes direction only at branches. Most graphs of graph-theoretic interest are undirected.  
  
__Weighted vs. Unweighted__  
Each edge (or vertex) in a weighted graph G is assigned a numerical value, or weight. The edges of a road network graph might be weighted with their length, drive-time, or speed limit, depending upon the application. In unweighted graphs, there is no cost distinction between various edges and vertices.  
  
__Simple vs. Non-simple__  
Certain types of edges complicate the task of working with graphs. A self-loop is an edge (x, x) involving only one vertex. An edge (x, y) is a multiedge if it occurs more than once in the graph. Both of these structures require special care in implementing graph algorithms. Hence any graph that avoids them is called simple.  
  
__Sparse vs. Dense__  
Graphs are sparse when only a small fraction of the possible vertex pairs actually have edges defined between them. Graphs where a large fraction of the vertex pairs define edges are called dense. There is no official boundary between what is called sparse and what is called dense, but typically dense graphs have a quadratic number of edges, while sparse graphs are linear in size. Sparse graphs are usually sparse for application-specific reasons. Road networks must be sparse graphs because of road junctions. The most ghastly intersection I’ve ever heard of was the endpoint of only seven different roads. Junctions of electrical components are similarly limited to the number of wires that can meet at a point, perhaps except for power and ground.  
  
__Cyclic vs. Acyclic__  
An acyclic graph does not contain any cycles. Trees are connected, acyclic undirected graphs. Trees are the simplest interesting graphs, and are inherently recursive structures because cutting any edge leaves two smaller trees.  
  
__Embedded vs. Topological__  
A graph is embedded if the vertices and edges are assigned geometric positions. Thus, any drawing of a graph is an embedding, which may or may not have algorithmic significance.  
  
__Implicit vs. Explicit__  
Certain graphs are not explicitly constructed and then traversed, but built as we use them. A good example is in backtrack search. The vertices of this implicit search graph are the states of the search vector, while edges link pairs of states that can be directly generated from each other. Because you do not have to store the entire graph, it is often easier to work with an implicit graph than explicitly construct it prior to analysis.  
  
__Labeled vs. Unlabeled__  
Each vertex is assigned a unique name or identifier in a labeled graph to distinguish it from all other vertices. In unlabeled graphs, no such distinctions have been made.  
  
###Traversing a Graph  
Each vertex will exist in one of three states:
* __undiscovered__ the vertex is in its initial, virgin state.
* __discovered__ the vertex has been found, but we have not yet checked out all its incident edges.
* __processed__ the vertex after we have visited all its incident edges.
  
__Depth-First Search__  
Depth-First Search for a graph is similar to Depth First Traversal of a tree. The only catch here is, unlike trees, graphs may contain cycles, so we may come to the same node again. To avoid processing a node more than once, we use a boolean visited array.
  
To visit a vertex v :
* Mark vertex v as visited.  
* Recursively visit all unmarked vertices adjacent to v.  

__Breadth-first Search__  
Breadth First Traversal for a graph is similar to Breadth First Traversal of a tree. The only catch here is, unlike trees, graphs may contain cycles, so we may come to the same node again. To avoid processing a node more than once, we use a boolean visited array. For simplicity, it is assumed that all vertices are reachable from the starting vertex.  
  
Repeat until queue is empty:
* Remove vertex v from queue.
* Add to queue all unmarked vertices adjacent to v and mark them.
  
__Topological Sorting__  
Topological ordering of a directed graph is a linear ordering of its vertices such that for every directed edge uv from vertex u to vertex v, u comes before v in the ordering.  
  
__Strongly Connected Components__  
Vertices v and w are strongly connected if there is both a directed path from v to w and a directed path from w to v.  
A strong component is a maximal subset of strongly-connected vertices.  
  
Strong connectivity is an equivalence relation:  
* v is strongly connected to v.  
* If v is strongly connected to w, then w is strongly connected to v.  
* If v is strongly connected to w and w to x, then v is strongly connected to x.  
  
__Minimum Spanning Tree__  
Connecting all the vertices together with the minimal total weighting for its edges.  
* Greedy MST algorithm
* Kruskal's algorithm
  1. Sort the Edges by weight.
  2. Go thought the sorted and build ur spanning tree, add edge as long as it doesn't create a cycle.
* Prim's algorithm

__Shortest Paths__
* Dijkstra's Algorithm

__Dynamic Programming__  
Dynamic Programming is an algorithmic paradigm that solves a given complex problem by breaking it into subproblems and stores the results of subproblems to avoid computing the same results again. Following are the two main properties of a problem that suggest that the given problem can be solved using Dynamic programming. 
* Overlapping Subproblems  
* Optimal Substructure  

___Overlapping Subproblems___ Like Divide and Conquer, Dynamic Programming combines solutions to sub-problems. Dynamic Programming is mainly used when solutions of same subproblems are needed again and again. In dynamic programming, computed solutions to subproblems are stored in a table so that these don’t have to recomputed. So Dynamic Programming is not useful when there are no common (overlapping) subproblems because there is no point storing the solutions if they are not needed again. For example, Binary Search doesn’t have common subproblems. If we take example of following recursive program for Fibonacci Numbers, there are many subproblems which are solved again and again.
There are following two different ways to store the values so that these values can be reused
* Memoization (Top Down): 
* Tabulation (Bottom Up):

___Memoization (Top Down)___ The memoized program for a problem is similar to the recursive version with a small modification that it looks into a lookup table before computing solutions. We initialize a lookup array with all initial values as NIL. Whenever we need solution to a subproblem, we first look into the lookup table. If the precomputed value is there then we return that value, otherwise we calculate the value and put the result in lookup table so that it can be reused later.  

___Tabulation (Bottom Up)___ The tabulated program for a given problem builds a table in bottom up fashion and returns the last entry from table.  

Both tabulated and Memoized store the solutions of subproblems. In Memoized version, table is filled on demand while in tabulated version, starting from the first entry, all entries are filled one by one. Unlike the tabulated version, all entries of the lookup table are not necessarily filled in memoized version.  

___Optimal Substructure___ A given problems has Optimal Substructure Property if optimal solution of the given problem can be obtained by using optimal solutions of its subproblems.  
