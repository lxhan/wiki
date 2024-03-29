[##](##) Notes from `Grokking algorithms`

### Intro

- `O(log n)` is faster than `O(n)`, but it gets a lot faster once the list of items you are searching through grows.
- Algorithm speed isn't measured in seconds.
- Algorithm times are measured in terms of growth of an algorithm.
- Algorithm times are written in Big O notation.

### Binary search

Binary search is an efficient algorithm for finding an item from a sorted list of items. It works by repeatedly dividing in half the portion of the list that could contain the item, until you've narrowed down the possible locations to just one

- Binary search is a lot faster than simple search.


### Selection sort

In selection sort, the first smallest element is selected from the unsorted array and placed at the first position. After that second smallest element is selected and placed in the second position. The process continues until the array is entirely sorted.

- Computer's memory is like a giant set of drawers.
- When you want to store multiple elements, use an array or a list.
- With an array, all your elements are stored right next to each other.
- With a list, elements are strewn all over, and one element stores the address of the next one.
- Arrays allow fast reads.
- Linked lists allow fast inserts and deletes.
- All elements in the array should be the same type.

### Recursion

- Recursion is when a function calls itself.
- Every recursive function has 2 cases: base case and recursive case.
- A stack has 2 operations: push and pop.
- All function calls go onto the call stack.
- The call stack can get very large, which may lead to stack overflow.

### Quick sort

Quick sort is a fast sorting algorithm that works by splitting a large array of data into smaller sub-arrays. This implies that each iteration works by splitting the input into two components, sorting them, and then recombining them.

- Divide & conquer works by breaking a problem down into smaller and smaller pieces. If you are using D&C on a list, the base case is probably an empty array with one element.
- If you are implementing quicksort, choose a random element as the pivot. The average runtime of quicksort is `O(n log n)`.
- The constant in Big O notation can matter sometimes. That's why quicksort is faster than merge sort.
- The constant almost never matters for simple search vs binary search, because `O(log n)` is so much faster than `O(n)` when your list gets big.

### Hash tables

- You can make hash table by combining a hash function with an array
- Hash tables need hash function that minimizes collisions
- Really fast search, insert and delete
- When load factor is greater than 0.7, it's time to resize hash table

Good for
- Modeling relationships from one thing to another thing
- Filtering out duplicates
- Caching/memorizing data instead of making your server do work

### Breadth first search

- Breadth first search tells you if there is a path from A to B and find the shortest
- If you have a problem like "find the shortest x", try modeling your problem as a graph, and use breadth first search to solve
- A directed graph has arrows and the relationship follows the direction of the arrow
- Undirected graphs don't have arrows and the relationship goes both ways
- Queues are FIFO
- Stacks are LIFO
- To find the shortest path we must check in the order nodes are added to the search list
- Once checked make sure you don't check same node again, otherwise you might end up in an infinite loop
- Running time of breadth first search is `O(V + E)`, where V for number of vertices and E for number of edges

### Dijkstra

Dijkstra's algorithm has 4 steps:
- Find cheapest node. This is the node you can get to in the least amount of time
- Check whether there's a cheaper path to the neighbors of this node and if so update their cost
- Repeat until you've done this for every node in the graph
- Calculate the final path 
  
- Breadth first search is used to calculate the shortest path for an unweighted graph
- Dijkstra's algorithm is used to calculate the shortest path for a weighted graph
- Dijkstra's algorithm works when all the weights are positive
- For negative weights use Bellman-Ford algorithm

### Greedy algorithms

- Greedy algorithms optimize locally, hoping to end up with a global optimum
- NP-complete problems have no known fast solution
- For NP-complete problems use approximation algorithm

### Dynamic programming

- Dynamic programming is useful when you are trying to optimize something given a constraint
- You can use DP when the problem can be broken into discrete subproblems
- Every DP solution involves a grid
- The values in the cells are usually what you are trying to optimize
- Each cell is a subproblem
- There is no single formula for calculating a DP solution

Uses cases:
- The longest common subsequence is being used to find similarities in DNA strands
- git diff
- Levenstein distance

### K-nearest neighbors

- KNN is used for classification and regression and involves looking at the k-nearest neighbors
- Classification = categorization into a group
- Regression = predicting a response
- Feature extraction means converting an item into a list of numbers that can be compared
