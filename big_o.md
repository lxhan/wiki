# Big O

- [Great video explanation](https://www.youtube.com/watch?v=kS_gr2_-ws8)

## Algorithms complexity
- Constant `O(1)` (ideal)
- Logarithmic `O(log n)` (excellent)
- Linear `O(n)` (ok)
- Quadratic `O(n^2)` (bad)
- Exponential `O(2^n)`
- Factorial `O(n!)`

## Shorthands
1. Arithmetic operations are constant
2. Variable assignment is constant
3. Accessing elements in an array (by index) or object (by key) is constant
4. In a loop, the complexity is the length of the loop times the complexity of whatever happens inside of the loop

## Examples
```js
// O(1)
const a = 2 + 3;

// O(n)
for (let i = 0; i < n; i++) {}

// O(n)
let a = 0;
for (let i = 0; i < n; i++) {
    // O(1)
    a += 1;
}

// O(n^2)
for (let i = 0; i < n i++) {
    for (let j = 0; j < m; j++) {
    
    }
}

// O(n)
for (let i = 0; i < n; i++) {}
for (let i = 0; i < n; i++) {}
for (let i = 0; i < n; i++) {}

// O(log n)
while (n > 0) {
   n /= 2; 
}

// O(nlog n)

// O(n)
for (let i = 0; i < n; i++) {
    // O(log n)
    while (x > 0) {
        x /= 2 
    }
}


// ---
// O(n)
function search(value, list) {
    // O(1)
    let fount = false;
    let position = -1;
    let index = 0;
   
    // O(n)
    while(!found && index < list.length) {
        O(1) 
        if (list[index] == value) {
            found = true;
            position = index;
        } else {
            index += 1;
        }
    }
    return position;
}
```
