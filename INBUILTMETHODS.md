# Inbuilt Methods

## Methods for Strings

1. length (property)
2. toUpperCase
3. toLowerCase
4. trim
5. substring
6. substr
7. includes

### Strings to Array

1. split

### Array to strings

1. join

---

## Methods for Numbers

1. toFixed
2. parseInt (takes number as input and returns integer)
   > Types of coercion:
   > a. Implicit Coercion: internal type conversion
   > b. Explicit Coercion: type conversion done by programmer

### String to Number

1. Number or +
   > If Number('str124'); returns NaN

## Object

1. delete someObj.keyName
2. hasOwnProperty
3. Object.keys
4. Object.values

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
