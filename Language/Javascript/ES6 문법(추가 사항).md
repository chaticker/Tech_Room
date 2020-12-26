### The let keyword
```javascript
var x = 10;
// Here x is 10
{ 
  let x = 2;
  // Here x is 2
}
// Here x is 10
```

### The const keyword
```javascript
var x = 10;
// Here x is 10
{ 
  const x = 2;
  // Here x is 2
}
// Here x is 10
```

### JavaScript Arrow Functions
```javascript
// ES5
var x = function(x, y) {
   return x * y;
}

// ES6
const x = (x, y) => x * y;

const x = (x, y) => { return x * y };
```

### JavaScript Class
```javascript
class ClassName {
  constructor() { ... }
}

class Car {
  constructor(name, year) {
    this.name = name;
    this.year = year;
  }
}

//using a class
let myCar1 = new Car("Ford", 2014);
let myCar2 = new Car("Audi", 2019);
```

### JavaScript Promise
```javascript
let myPromise = new Promise(function(myResolve, myReject) {
// "Producing Code" (May take some time)

  myResolve(); // when successful
  myReject();  // when error
});

// "Consuming Code" (Must wait for a fulfilled Promise).
myPromise.then(
  function(value) { /* code if successful */ },
  function(error) { /* code if some error */ }
);

//using a promise
let myPromise = new Promise(function(myResolve, myReject) {
  setTimeout(function() { myResolve("I love You !!"); }, 3000);
});

myPromise.then(function(value) {
  document.getElementById("demo").innerHTML = value;
});
```

### JavaScript Symbol
```javascript
const person = {
  firstName: "John",
  lastName: "Doe",
  age: 50,
  eyeColor: "blue"
};

let id = Symbol('id');
person.id = 140353;
```

### Default Parameter Values
```javascript
function myFunction(x, y = 10) {
  // y is 10 if not passed or undefined
  return x + y;
}
myFunction(5); // will return 15
```

### Function Rest Parameter
```javascript
function sum(...args) {
  let sum = 0;
  for (let arg of args) sum += arg;
  return sum;
}

let x = sum(4, 9, 16, 25, 29, 100, 66, 77);
```

### Array.find()
```javascript
var numbers = [4, 9, 16, 25, 29];
var first = numbers.find(myFunction);

function myFunction(value, index, array) {
  return value > 18;
}
```

### Array.findIndex()
```javascript
var numbers = [4, 9, 16, 25, 29];
var first = numbers.findIndex(myFunction);

function myFunction(value, index, array) {
  return value > 18;
}
```

### New Number Properties
```javascript
var x = Number.EPSILON;

var x = Number.MIN_SAFE_INTEGER;

var x = Number.MAX_SAFE_INTEGER;
```

### New Number Methods
```javascript
//Number.isInteger()
Number.isInteger(10);        // returns true
Number.isInteger(10.5);      // returns false

//Number.isSafeInteger()
Number.isSafeInteger(10);    // returns true
Number.isSafeInteger(12345678901234567890);  // returns false
```

### New Global Methods
```javascript
//isFinite()
isFinite(10/0);       // returns false
isFinite(10/1);       // returns true

//isNaN()
isNaN("Hello");       // returns true
```
