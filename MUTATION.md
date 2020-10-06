# Mutation in JavaScript

## Immutable

- If a change in the reference does not change the original and vice versa, it is called immutable behavior.
- Primitive Data types are immutable.
- Example:

```js
var a = "You cannot change me from the reference";
var b = a;
b = "a is immutable";
console.log(a); // You cannot change me from the reference
console.log(b); // a is immutable
```

## Mutable

- If a change in the reference changes the original and vice versa, it is called mutable behavior.
- Arrays and Objects are examples of mutable data types.

* Example:

```js
var student = {
  name: "Ram",
  class: 9,
  roll: 2,
};

var newStudent = student;

newStudent.group = "red";
// now student and newStudent both have group: red
console.log(student.group); // red
console.log(newStudent.group); //red

student.status = "pass";
// now student and newStudent both have status: pass
console.log(student.status); // pass
console.log(newStudent.status); // pass
```
