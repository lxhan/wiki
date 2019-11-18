- Find longest line of text
```js
let longestUnit = lines.reduce((a, b) => (a.length > b.length ? a : b));
```

# ES6-8
* __Arrow functions__
  1. Light version of usual functions
  2. Compact syntax `x => x * x`
  3. Save lexical meaning of `this`
  4. Doesn't have `prototype`, can't be called with `new` keyword


* __Rest parameter__
  1. `function f(a, b, ...c)`
  2. Type array (may be empty)
  3. Should go last in list
  4. One rest param max


* __Spread__
  1. Spread array converting it to list of arguments
  2. `const max = Math.max(...arr)`


* __Object desctructuring__
  ```js
  function connect({
    host = 'localhost',
    port = 3333,
    user = 'guest'
  } = {}) {
  
  }
  ```
* __Array destructuring__
  `const [a, b] = [1, 2]`


* __Object shallow copy__
  ```js
  const obj1 = {
    name: 'alex',
    age: 32,
    occupation: 'engineer'
  };
  
  const obj2 = {
    position: 'manager',
    language: 'english'
  };
  
  const val = Object.assign({}, obj1, obj2);
  ```

* __Object spread__
  `const val = { ...obj1, ...obj2 };`
  
  
* __Prototypes__
  1. `Object.setPrototypeOf(obj, proto)`
  2. `const obj = Object.create(proto)`
  3. `const obj = new Something()`
  `Something.prototype` becomes prototype of `obj`
  

# React
- __Create__
  1. `src/index.js` - main file
  2. `public/index.html` - html template
  3. `package.json` - for dependencies
  4. All other files can be deleted


- __JSX__
  1. Camel case attributes
  2. `className` and `htmlFor` are the only 2 differences


- __Arrays and keys__
  1. React uses `key` to effectively compare elements when updating
  2. Not recommended to make keys from array indexes


- __npm start error__
  1. `npm cache clean --force` 
  2. `rm -rf node_modules`
  3. `npm i && npm start`
