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
