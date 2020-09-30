# Scopes in JavaScript

- Global Scope
- Functional or Local Scope
- Block Scope

---

## Global Scope

- Variables, objects and functions declared in global scope are accessible in any part of the file.

### Example:

```js
var globalVariable = "I am a global variable";

let globalVariableDeclaredWithLet =
  "I am a global variable declared with let keyword";

const globalConstant = "I am a global constant";

function globalFunction() {
  console.log("I am a global function");
}
```

- In above example, all the variables, const and functions have global scope which means we can access them from anywhere in that file.

---

## Functional or Local Scope

- Variables, objects and functions declared inside a function have functional scope.
- The variables can be accessed inside that function only.

### Example:

```js
function globalFunction() {
  var localVariable = "I am a local variable";

  let localVariableDeclaredWithLet = "I am a local variable declared with let";

  function localFunction() {
    console.log(
      "I am a local function and I can be called within this function only"
    );
  }

  localFunction(); //  I am a local function and I can be called within this function only
}
// invoking localFunction outside the function
localFunction(); // ReferenceError: localFunction is not defined.
```

---

## Block Scope:

- Variables, objects and functions declared inside if, while, for etc block of code.
- Variables, objects and functions are accessible within that block only.

### Example:

```js
if(true) {
  let blockVariable = "I am a block variable";
  let blockFunction = () {
    console.log("I am a block function");
  }
  // blockFunction can be called here
  blockFunction(); //I am a block function
}
// blockFunction cannot be called outside the block
blockFunction(); //ReferenceError: blockFunction is not defined
```

---

## Weird Behavior of '_var_'

- Variables declared with keyword _var_ donot maintain a block scope.

### Exampe:

```js
if (true) {
  var iAmWeird = "I am weird and you can access me from outside this block.";
}

//  iAmWeird can be accessed outside the block.
console.log(iAmWeird); // I am weird and you can access me from outside this block.
```

---

## Declared without any keyword

- Variables, functions, objects declared without any keyword do not maintain block scope and can be accessed outside the block.

### Example:

```js
if (true) {
  iAmWeird = "I am weird and you can access me from outside this block.";

  function weirdFunction() {
    console.log(
      "I am a weird function and you can call me from outside this block"
    );
  }
}

console.log(iAmWeird); // I am weird and you can access me from outside this block.

weirdFunction(); // I am a weird function and you can call me from outside this block
```

---

## _let_ and _const_

- The behavior of _var_ not maintaining a block scope, can bring many issues in our code.
- _let_ and _const_ comes to the rescue for this type of behavior of _var_.
- _let_ and _const_ maintain the block scope.

### Example:

```js
if (true) {
  let iAmNotWeird =
    "I am not weird and you cannot access me from outside this block.";

  const notWeirdFunction = function () {
    console.log(
      "I am  not a weird function and you cannot call me from outside this block"
    );
  };
}

// cannot be accessed outside the _if_ block.
console.log(iAmNotWeird); // ReferenceError: iAmWeird is not defined.
notWeirdFunction(); // ReferenceError: weirdFunction is not defined.
```

---
