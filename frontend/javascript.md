# JavaScript

* Find longest line of text

  ```javascript
  let longestUnit = lines.reduce((a, b) => (a.length > b.length ? a : b));
  ```

## ES6-8

* **Arrow functions**
  1. Light version of usual functions
  2. Compact syntax `x => x * x`
  3. Save lexical meaning of `this`
  4. Doesn't have `prototype`, can't be called with `new` keyword
* **Rest parameter**
  1. `function f(a, b, ...c)`
  2. Type array \(may be empty\)
  3. Should go last in list
  4. One rest param max
* **Spread**
  1. Spread array converting it to list of arguments
  2. `const max = Math.max(...arr)`
* **Object desctructuring**

  ```javascript
  function connect({
    host = 'localhost',
    port = 3333,
    user = 'guest'
  } = {}) {

  }
  ```

* **Array destructuring**

  `const [a, b] = [1, 2]`

* **Object shallow copy**

  ```javascript
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

* **Object spread** `const val = { ...obj1, ...obj2 };`
* **Prototypes**
  1. `Object.setPrototypeOf(obj, proto)`
  2. `const obj = Object.create(proto)`
  3. `const obj = new Something()`

     `Something.prototype` becomes prototype of `obj`

## React

* **Create**
  1. `src/index.js` - main file
  2. `public/index.html` - html template
  3. `package.json` - for dependencies
  4. All other files can be deleted
* **JSX**
  1. Camel case attributes
  2. `className` and `htmlFor` are the only 2 differences
* **Arrays and keys**
  1. React uses `key` to effectively compare elements when updating
  2. Not recommended to make keys from array indexes
* **npm start error**
  1. `npm cache clean --force` 
  2. `rm -rf node_modules`
  3. `npm i && npm start`

