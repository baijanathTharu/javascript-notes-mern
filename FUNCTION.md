# Functions in JavaScript

- Functions are reusable block of codes that performs specific tasks.

## Two ways of writing a function

1. Expression Syntax

```js
var a = function () {
  console.log("I am a function written with expression syntax");
};
```

2. Declaration Syntax

```js
function welcome() {
  console.log("I am a function written with declaration syntax");
}
```

## Types of Functions

### 1. Named Function

- Function with name.

```js
var a = function () {
  console.log("My name is a");
};

function b() {
  console.log("My name is b");
}
```

### 2. Anonymous Function

- Function without any name

```js
function() {
  console.log('I don\'t have a name.');
}
```

### 3. Function with argument

- Function receving some argument.

```js
function welcome(name) {
  console.log("Hello ", name);
}
```

> Note::> if the number of argument is more than 3, try to reduce the size with single argument using object.

### Function with return type

- Function returning some values.

```js
function(x, y) {
  return x + y;
}
```

### IIFE

- Immediately Invoked Functional Expression
- Function invoked at the time of declaration itself.

```js
(function () {
  console.log("Anonymous function is immediately invoked.");
})();
```
