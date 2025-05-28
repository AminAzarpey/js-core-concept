
# JavaScript Core Concepts - Interview Prep

This README contains a comprehensive explanation of important JavaScript concepts from basic to advanced, suitable for interviews or deep learning.

---

## 1. Primitive vs Reference Types

**Primitive Types**: Number, String, Boolean, null, undefined, Symbol, BigInt. Stored by value.  
**Reference Types**: Objects, Arrays, Functions. Stored by reference.

---

## 2. Type Coercion

JS automatically converts types:
```js
'5' + 1     // '51' (string)
'5' - 1     // 4 (number)
false == 0  // true
```

Use `===` for strict comparison.

---

## 3. let / const vs var

- `var`: Function-scoped, hoisted
- `let`, `const`: Block-scoped, not hoisted
- `const` cannot be reassigned (but can mutate objects)

---

## 4. IIFE (Immediately Invoked Function Expression)

```js
(function() {
  console.log("Runs immediately");
})();
```

---

## 5. Iterators

Objects implementing `Symbol.iterator` and `.next()`:
```js
const arr = [1, 2];
const iter = arr[Symbol.iterator]();
iter.next(); // { value: 1, done: false }
```

---

## 6. Immutability

Avoid mutating state:
```js
const newArr = [...arr, 4]; // instead of arr.push(4)
```

---

## 7. Arrow Functions Limitations

- No own `this`
- No `arguments` object
- Can't be used as constructors

---

## 8. Timers: setTimeout, setInterval

```js
setTimeout(() => console.log("Once"), 1000);
const id = setInterval(() => console.log("Repeat"), 1000);
clearInterval(id);
```

---

## 9. Function Concepts

- **First-Class**: Functions can be passed like variables
- **Higher-Order**: Functions that take/return functions
- **Currying**:
```js
const add = a => b => a + b;
add(2)(3);
```

---

## 10. Bind, Call, Apply

```js
const fn = function(a, b) { console.log(this.x, a, b); };
fn.call({ x: 1 }, 2, 3);
fn.apply({ x: 1 }, [2, 3]);
const bound = fn.bind({ x: 1 }, 2);
bound(3);
```

---

## 11. Memoization

Caching results:
```js
function memo(fn) {
  const cache = {};
  return x => cache[x] ?? (cache[x] = fn(x));
}
```

---

## 12. Constructor / Class

```js
function Person(name) { this.name = name; }
const p = new Person("Ali");

class User {
  constructor(name) { this.name = name; }
}
```

---

## 13. `this` Keyword

Context depends on how a function is called:
- Global: `window`
- Method: object
- Arrow: lexical `this`

---

## 14. Inheritance

```js
class A {}
class B extends A {}
```

---

## 15. Prototype Chain

```js
obj.__proto__ => Object.prototype
```

---

## 16. Call Stack

LIFO stack where execution context is pushed/popped.

---

## 17. Execution Context

Created in 2 phases:
- Creation (scope, `this`, variables)
- Execution (run code)

---

## 18. Memory Heap

Where objects are stored dynamically.

---

## 19. Event Loop

Moves tasks from queues to the call stack when it's empty.

---

## 20. Callback Queue

setTimeout, setInterval => pushed here

---

## 21. Microtask Queue (Promises)

Promises, MutationObservers go here. Runs before callback queue.

---

## 22. Callbacks

Pass function as argument:
```js
function fetchData(cb) { cb("data"); }
```

---

## 23. Promises

```js
new Promise((resolve, reject) => resolve("done"))
  .then(data => console.log(data));
```

---

## 24. Async/Await

```js
async function load() {
  const data = await fetch('/api');
}
```

---

## 25. Promise Utilities

```js
Promise.all([p1, p2]);
Promise.race([p1, p2]);
Promise.allSettled([p1, p2]);
Promise.any([p1, p2]);
```

---

## 26. Web APIs

APIs provided by browser:
- DOM: `document.querySelector`
- Fetch: `fetch()`
- Storage: `localStorage`, `sessionStorage`
- Geo: `navigator.geolocation`
- History: `history.pushState`
