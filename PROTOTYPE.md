# Prototypes in JavaScript

## Types of OOP

1. Class Based OOP
2. Prototype Based OOP

## Class Based OOP

- Basic building block: class
- class has:
  - constructor: value initialization is done in constructor
  - fields(properties)
  - methods
- **Syntax**

```js
class Student {
  school = "XYZ"; // property
  class = 4; // property

  constructor() {
    // this is a constructor
  }

  someMethod() {
    // this is a method
  }
}
```

## Pillars of OOP

1. **Inheritance**: Getting access to properties and methods of other classes

1. **Encapsulation**: data hiding mehanism

1. **Polymorphism**: multiple forms of a single function

1. **Abstraction**: hide lower level complexities and show only high level function (e.g. In sendMail() function, user do not care how the email is being sent but only care about what sendMail does.)

## Prototype Based OOP

> functions in JavaScript have many names: closure, callback, hof, method, functional constructor(in Prototype)

- Basic Building Block: **functional constructor**

### Properties of Functional Constructor

- It does not return.
- It is called with _new_ keyword.

### this keyword

- 'this' has the object in which it is used.
- for e.g.

```js
console.log("this global: ", this); // this has global object.

// Student is a functional constructor here.
function Student() {
  this.school = "XYZ";

  //  here this has student object
  console.log("this Student: ", this); // {school: "XYZ"}
}

// we can call Student functional constructor with new keyword
// and make an instance of Student

// ram is an instance of Student
var ram = new Student();

// shyam is another instance of Student
var shyam = new Student();
```

---

## Prototypes

- Declaring a functional constructor called Books

```js
function Books {

}
```

- Anything added with this keyword inside the functional constructor is added to the constructor

```js
function Books() {
  // printedBy property is added to the constructor
  this.printedBy = "ABC Printing Company";
  // edition is added to the constructor
  this.edition = 2;
}
```

- We can add additional properties and methods to Books with **prototype** keyword as below:

```js
function Books() {
  this.printedBy = "ABC Printing Company";
  this.edition = 2;
}

// adding a property price to the Books
Books.prototype.price = 575;

// adding a method getPrice to the Books
Books.prototype.getPrice = function () {
  return this.price;
};
```

- Making an instance of Books

```js
//  below instance gets what is inside the constructor
// So we get printedBy and edition property of Books
var prayogSala = new Books();
```

- We can access **price** property and **getPrice** method using "."(dot)

```js
var prayogSala = new Books();
// to access price property
var prayogSalaPrice = prayogSala.price;
console.log("price is: ", prayogSalaPrice); // prints 575

// to access the getPrice method
var prayoSalaGetPrice = prayogSala.getPrice;
console.log("getPrice is ", prayoSalaGetPrice()); // prints 575
```

### GIST

- Array, object, string and number are functional construtors.
- For example we can make an instance of an array using _new_ keyword.

```js
var someArr = new Array();
// someArr is an instance of array
// so we can access all the property and
// methods of array using dot notation.
var someArrLength = someArr.length;
```

- We can also see how any method like **_forEach_**, **_toUpperCase_**, etc can be made with _prototype_ keyword and it can inherited by their respective functional constructor it as below:

```js
// forEach method is inherited by Array
Array.prototype.forEach = function () {};
```

```js
// toUpperCase method is inherited by String
String.prototype.toUpperCase = function () {};
```
