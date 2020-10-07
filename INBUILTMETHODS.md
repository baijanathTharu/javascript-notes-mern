# Inbuilt Methods

## Methods for Strings

1. length (property)

```js
var name = "Shyam";
var nameLength = name.length;
console.log(nameLength); // 5
```

2. toUpperCase

```js
var name = "Shyam";
var upperCaseName = name.toUpperCase();
console.log(upperCaseName); // SHYAM
```

3. toLowerCase

```js
var name = "Shyam";
var upperCaseName = name.toLowerCase();
console.log(upperCaseName); // shyam
```

4. trim
   > Remove spaces from beginning and end of the string.

```js
var name = " Sh yam  ";
var trimmedName = name.trim();
console.log(trimmedName); // Sh yam
```

5. substring
   > Syntax: someString.substring(includedInitialIndex, excludedLastIndex);

```js
var nationality = "Nepali";

// Finding country name using substring
var countryName = nationality.substring(0, 5);
console.log(countryName); // Nepal
```

6. substr
   > Syntax: someString.substr(fromWhichIndex, howMany);

```js
var profession = "programmer";

// Finding grammer using substr
var grammerFromProfession = profession.substr(3, 7);
console.log(grammerFromProfession); // grammer
```

7. includes
   > return true if element exist in the string, otherwise return false

```js
var countryName = "Nepal";
countryName.includes("p"); // true
countryName.includes("z"); // false
```

### Strings to Array

1. split
   > separate characters of string with specified character

```js
var fruitName = "Apple";

// separating each character
var separateEachCharacters = fruitName.split("");
console.log(separateEachCharacters); // ["A", "p", "p", "l", "e"]

// separating characters with 'l'
var separatedWithP = fruitName.split("l"); // ["App", "e"]
```

### Array to strings

1. join
   > join elements of an array with specified character

```js
var separatedCharacters = ["A", "p", "p", "l", "e"];

// Array to string
separatedCharacters.join(""); // Apple
```

---

## Methods for Numbers

1. toFixed
   > fixing the decimal places of a floating number.

```js
var someNumber = 3.141592;
var onlyThreeDecimalPlaces = someNumber.toFixed(3); // 3.142
```

2. parseInt (takes number as input and returns integer)
   > Types of coercion:
   > a. Implicit Coercion: internal type conversion
   > b. Explicit Coercion: type conversion done by programmer

```js
var pi = 3.14;
var integerPi = parseInt(pi); // 3
```

### String to Number

1. Number or +
   > If Number('str124'); returns NaN

```js
var stringNumber = "3";
var actualNumber = Number(stringNumber); // 3

// NaN: A Number datatype
var someString = "Shyam";
var stringToNum = Number(someString); // Nan
```

## Object

1. delete someObj.keyName

```js
var student = {
  name: "Shyam",
  class: 2,
  status: "Pass",
};

// Deleting the status property of the student object
delete student.status;
```

2. hasOwnProperty
   > return true if the property exist in the object, otherwise return false

```js
var student = {
  name: "Shyam",
  class: 2,
  status: "Pass",
};

student.hasOwnProperty("name"); // true
student.hasOwnProperty("group"); // false
```

3. Object.keys
   > returns an array of all the keys of the object as elements

```js
var student = {
  name: "Shyam",
  class: 2,
  status: "Pass",
};

var keysOfStudent = Object.keys(student);
console.log(keysOfStudent); // ["name", "class", "status"]
```

4. Object.values
   > returns an array of all the values of the keys of the object as elements

```js
var student = {
  name: "Shyam",
  class: 2,
  status: "Pass",
};

var valuesOfKeys = Object.values(student);
console.log(valuesOfKeys); // ["Shyam", 2, "Pass"]
```

### Object Serialization

1. Serialized Object
2. DeSerialized Object

```js
var serilizedObj = JSON.stringify(obj);
console.log("original object", obj);
console.log("string representation>>", serilizedObj);
console.log("deserilized >>", JSON.parse(serilizedObj));
```

- JSON.stringify and JSON.parse always cames in pair
