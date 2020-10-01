# Datatype

## Introduction

- Datatype is a classification of data.

## Types of Datatypes

### 1. Primitive

- Number: 1, 2.2
- Boolean: true or false
- String: any single or double quote enclosed value
- Undefined: memory allocated but value is not defined
- Null: memory not allocated
- Symbol: used for maintaining unique keys in objects.

### 2. Non primitive

- Array: ['Ram', 'Shyam']

* Object: {{name: 'Ram', id: 1}, {name: 'Shyam', id: 2}}

---

#### Array

- Datatype holding multiple values.
- Syntax

```js
// Constructor syntax
var a = new Array();

// bracket notation syntax
var b = [];
```

- Arrays in JavaScript are **Heterogenous** (mixed values) arrays.
  Exampe:

```js
var xyz = ["hi", true, 33, null, undefined, []];
```

- The elements of array can be accessed by index starting from 0.

---

#### Objects

- Object is a collection of key value pair.
- Syntax

```js
// Constructor syntax
var obj = new Object();

// Bracket notation syntax
var newObj = {};
```

- Example:

```js
var student = {
  name: "ramesh",
  age: 33,
  hobbies: ["singing", "coding"],
  presentStatus: true,
};
```

> _name_, _age_, _hobbies_, _presentStatus_ are keys.
> _ramesh_, _33_, _["singing", "coding"]_, _true_ are values.

#### Accessing value of an Object

##### 1. Dot notation

> Example: _student.name_, _student.hobbies_, _student.car_

##### 2. Bracket notation

> Example: _student['name']_, _student['hobbies']_, _student['car']_
