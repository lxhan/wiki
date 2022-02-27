## Time complexity equation

Works by inserting the size of the data set as an integer `n`, and returning the number of operations than need to be conducted by the computer before the function can finish.

Measure efficiency based on 4 metrics:

* Accessing equation
* Searching equation
* Inserting equation
* Deleting equation

## Array

- Accessing: `O(1)`
- Searching: `O(n)` (linear search)
- Inserting, Deleting: `O(n)`

### Pros

- Good for storing similar contiguous data
- `O(1)` access

### Cons

- Size of the array can't be changed once initialized
- Inserting and Deleting are not efficient
- Can be wasting storage space


## ArrayList 

The ArrayList can be thought of as a growing array.

## Stack

Sequential access data structure in which we add and remove elements according to LIFO (last in first out)

Stack has 2 operations: push and pop

All function calls go onto the call stack

Real world example: undo/redo

- Accessing, Searching: `O(n)`
- Inserting, Deleting: `O(1)`

## Queue

Sequential access data structure in which we add and remove elements according to FIFO (first in first out)

Real world example: job schedule

- Accessing, Searching: `O(n)`
- Inserting, Deleting: `O(1)`


## LinkedList

Sequential access linear data structure in which every element is a separate object called a Node, which has 2 parts: data and reference (pointer) which points to the next Node in the List.

Real world example: can be used in the backing of other data structures; to make Stacks, Queues etc. (songs in playlist, image viewer)

- Accessing, Searching, Inserting, Deleting: `O(n)`

## Doubly LinkedList

Almost the same as LinkedList except that it able to traverse both forwards and backwards using pointers.

Real world example: undo/redo, recent history.


## Dictionary

Abstract data structure which stores data in key/value pairs.

## Tree

Trees store data hierarchically as opposed to linearly.

Real world example: linux directory structure

- Vertice - A certain Node in a Tree
- Edge - A connection between Nodes
- Root Node - Topmost Node of a Tree.
- Child Node - A certain Node which has an edge connecting it to another Node one level above itself
- Parent Node - Any Node which has 1 or more child Nodes
- Leaf Node -  A Node in a Tree which doesn't have any child Nodes
- Height - Number of edges on the longest possible path down towards a leaf
- Depth - Number of edges required to get from that particular Node to the root Node

### Binary Search Tree

Simple variation on the standard tree which has 3 restrictions:

1. A Node can have at most 2 children
2. For any given parent Node, the child to the left has a value less than or equal to itself and the child to the right has a value greater than or equal to itself
3. No 2 Nodes can contain the same value

The biggest advantage of BST is that it is possible to search through them in logarithmic time.
Good to use for storing large quantities of data that need to be easily searchable.

### Trie

Tree-like data structure whose nodes store letters of an alphabet in the form of characters.

Real world example: autocompletion, autocorrection etc

### Heap

Special tree where all parent Nodes compare to their children Node's in some specific way by being more or less extreme.

Heaps are commonly used in HeapSort, a sorting algorithm which takes in a list of elements, builds them into a min or max heap and then removes the root Node continuosly to make a sorted list.

Priority queues: advanced data structure which computer uses to designate tasks and assign power based on how urgent the matter is.

- Either greater than or less than
- Determines where the data is stored
- Usually dependent on the parent Node's value

#### Min-Heap

- The value at the root Node of the tree must be the minimum amongst all of its children
- This fact must be the same recursively for all parent Node's contained within heap

#### Max-Heap 

Exact opposite of min-heap


## Graph

Non linear data structure consisting of Nodes and Edges.

The main difference with Tree is that Graph has no starting point.

Types of Graphs:

- Directed / Undirected
- Cyclic / Acyclic
- Weighted Edges / Unweighted Edges

### Undirected Graph

Direction in which you traverse the Nodes isn't important.

### Cyclic Graph

One which contains a path from at least one Node back to itself.

All undirected graphs are cyclical.

#### Undirected Cyclical Heaps with Weighted Edges 

Can be used through Dijkstra's shortest path algorithm.
Compiles a list of the shortest possible paths from that source vertex to all other Nodes within the Graph.

Real world example: Google maps

#### Unweighted Cyclical Graphs 

Used in the follower system in social networks.
