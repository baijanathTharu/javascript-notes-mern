## Example:

```js
add(2, 6); // 8

function add(x, y) {
  return x + y;
}
```

- We called the _add_ function even before declaring it. This is possible in JavaScript because of Hoisting feature.
- In **hoisting**, all the declarations are moved to the top of the current scope.
- It is not only applicable to functions but to any other variables.
- We can use any variable even before declaring it. For example:

```js
num1 = 2;
console.log(num1); // 2
var num1;
```

## Hoisting in Action

```js
num1 = 2;
num2 = 6;
add(num1, num2); // 8
var num1;
var num2;
function add(x, y) {
  return x + y;
}
```

## _let_ and _const_

```js
num1 = 2;
console.log(num1); // ReferenceError: Cannot access 'num1' before initialization
let num1;
```

- With _let_ and _const_, we cannot use the variable before its declaration. If we try to use, we get _RefrenceError_ as above.
- This is because of hoisting in which the variables declared with _let_ and _const_ are moved to the top and are only declared but not initialized and hence _ReferenceError_.
