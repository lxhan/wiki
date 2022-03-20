## Notes from `Grokking algorithms`

### Intro

- Binary search is a lot faster than simple search.
- `O(log n)` is faster than `O(n)`, but it gets a lot faster once the list of items you are searching through grows.
- Algorithm speed isn't measured in seconds.
- Algorithm times are measured in terms of growth of an algorithm.
- Algorithm times are written in Big O notation.

### Selection sort

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
