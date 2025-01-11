# JavaScript Cheat Sheet

## 1. **Variables**

- **Declaration**: `let`, `const`
  - `let` - block-scoped, mutable
  - `const` - block-scoped, immutable

## 2. Data Types

- **Primitive**: `string`, `number`, `bigint`, `boolean`, `undefined`, `null`, `symbol`, `Object`.

## 3.Functions

- **Standard function**:

```javascript
function greet(name) {
  return `Hello ${name}!`;
}
```

> **_Arrow Function_**:
>
> > ```javascript
> > const greet = (name) => `Hello ${name}!`;
> > ```

## 4. Destructuring

- **Arrays**:

```javascript
const [a, b] = [1, 2];
```

- **Objects**

```javascript
const { key } = { key: "value" };
```

> **_Alias_**
>
> > ```javascript
> > const { key: alias } = { key: "value" };
> > ```

## 5. Spread & Rest Operator

- **Spread Operator**:
  > _expands an iterable_

```javascript
const arr1 = [1, 2];
const arr2 = [...arr1, 3];
```

- **Rest Operator**:
  > _allows a function to treat an indefinite number of arguments as an array_

```javascript
function sum(...nums) {
  return nums.reduce((a, b) => a + b);
}
```

## 6. Modules

- Export:

```javascript
export const greet = () => {};
```

- Import:

```javascript
import { greet } from "./file.js";
```

## 7. Promises and Async/Await

- **Promise**:
  > _an object that may produce a value in the **future** either as a `resolve` or as a `reject`._

```javascript
fetch(url)
  .then((res) => res.json())
  .catch((err) => console.error(err));
```

- **Async/Await**:
  > _`async` makes a function return a **Promise**._  
  > _`await` makes a function wait a **Promise**._

```javascript
async function fetchData() {
  try {
    const res = await fetch(url);
  } catch (err) {
    console.error(err);
  }
}
```

## 8. Classes

- A class need a `constructor`.

```javascript
class Person {
  constructor(name) {
    this.name = name;
  }
  greet() {
    return `Hi, I'm ${this.name}`;
  }
}
```

## 9. Array Methods

- `map`, `filter`, `reduce`, `find`, `forEach`:

```javascript
const arr = [1, 2, 3];
const squares = arr.map((x) => x ** 2);
```

## 10. Optional Chaining

> _Simplify accessing the property and deals with potential_ `null` _or_ `undefined` _value._

```javascript
const user = {};
console.log(user?.profile?.email);
```

## 11. Nullish Coalescing

> _Returns its **right-hand side** operand when its left-hand side operand is_ `null` _or_ `undefined`_.  
> Else, returns its left-hand side operand._

```javascript
const val = null ?? "default"; // 'default'
```

## 12. Short-Circuit Evaluation

- `||` (OR) and `&&` (AND):

```javascript
const a = null || "default"; // 'default'
const a = null && "default"; // null
```

## 13. DOM Manipulation

```javascript
document.querySelector("#id").textContent = "Hello";
```

## 14. Event Listeners

```javascript
element.addEventListener("click", (e) => console.log("Clicked"));
```

## 15. Error Handling

```javascript
try {
  riskyCode();
} catch (err) {
  console.error(err);
} finally {
  cleanup();
}
```

## 16. ES6+ Features

-**Set/Map**:

```javascript
const set = new Set([1, 2]);
const map = new Map([["key", "value"]]);
```

- **Symbol**:

```javascript
const sym = Symbol("desc");
```

## 17. JSON

- **Parse**:

```javascript
const obj = JSON.parse('{"key":"value"}');
```

- **Stringify**:

```javascript
const str = JSON.stringify({ key: "value" });
```

## 18. Timers

```javascript
setTimeout(() => console.log("Delay"), 1000);
setInterval(() => console.log("Repeat"), 1000);
```

## 19. Debugging

```javascript
console.log();
```
