# Closures in JavaScript

- Closures are the functions defined inside a function.
- For example: In the code below, _innerFunction_ is a closure.

```js
function outerFunction() {
  function innerFunction() {
    let text = "I am a closure";
    return text;
  }
  let text = "I am an outer function";
  return text;
}
```

---

## Making closure accessible from outside the functional scope

- Invoking _outerFunction_ will return a text _"I am an outer function"_.
- We can invoke the _innerFunction_ inside the _outerFunction_.
- But how can we invoke the innerFunction from the global scope?
- In order to do so, instead of returning a text in _outerFunction_, we can return the _innerFunction_ itself as below:

```js
function outerFunction() {
  function innerFunction() {
    let text = "I am a closure";
    return text;
  }
  return innerFunction;
}
```

- Now we have access to the _innerFunction_.

```js
// invoking outerFunction to get access to _innerFunction_
console.log(outerFunction()); // returns [Function: innerFunction]
// This shows we have access to the _innerFunction_
```

- If we invoke _outerFunction_, with two parenthesis, we can see the variable text defined inside _innerFunction_ returned as below:

```js
console.log(outerFunction()()); // return "I am a closure"
```

---

- We can have closures penetrating deep inside a function. It is also called currying.
- For example:

```js
function addition(num1) {
  var addition2 = function (num2) {
    var addition3 = function (num3) {
      return num1 + num2 + num3;
    };
    return addition3;
  };
  return addition2;
}

console.log("3 + 3 + 3 = ", addition(3)(3)(3)); // returns 9
console.log("4 + 5 + 6 = ", addition(4)(5)(6)); // return 15
```
