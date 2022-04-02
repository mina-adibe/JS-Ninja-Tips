###### 1. await - promise.all

:x:

```javascript
const user = await getUser();
const product = await getProducts();
```

:white_check_mark:

> Up to twice as faster

```javascript
const [user, products] = await Promise.all([getUser(), getProducts()]);
```

---

###### 2. Double Negation (!!)

```javascript
const greeting = "Hello there! ";
console.log(!!greeting); // returns true
```

```javascript
const noGreeting = "";
console.log(!!noGreeting); // returns false
```

---

###### 3. use object.entries to access both key and value

:x:

```javascript
object.keys(obj).forEach((key) => {
  const value = obj[key];
  // log out "key" and "value"
  console.log(key, value);
});
```

:white_check_mark:

```javascript
object.entries(obj).forEach(([key, value]) => {
  // log out "key" and "value"
  console.log(key, value);
});
```

---

###### 4. Don't use optional function call

:x:

```javascript
function calIfCallable(callback){
  callback?.()
}
});
```

:white_check_mark:

```javascript
function calIfCallable(callback){
 if(typeof callback === "function" ){
  callback();
 }
}
});
```

---

###### 5. Enums in javascript

```javascript
const Days = object.freeze({
  MONDAY: 0,
  TUESDAY: 1,
  WEDNESDAY: 2,
  THURESDAY: 3,
  FRIDAY: 4,
  SATURDAY: 5,
  SUNDAY: 6,
});
```

---

###### 6. Map on array of objects using ARRAY.FROM

```javascript
const avengers = [
  { name: "Ironman", power: "Armor", id: 1 },
  { name: "Thor", power: "Hammer", id: 2 },
  { name: "Hulk", power: "Strength", id: 3 },
];

Array.from(avengers, ({ name }) => name);
//["Ironman" ,"Thor" , "Hulk" ]
```

---

###### 7. Add to clipboard

:x: no need to copy from the dom anymore

```javascript
document.execcommand("example of text ");
```

:white_check_mark: supported by all major browsers

```javascript
navigator.clipboard.writeText("example of text ");
```

---

###### 8. Number truncation in javascript

```javascript
const number = 80.6;
// old ways
number < 0 ? Math.ceil(number) : Math.floor(number);
//80
```

```javascript
const es6 = Math.turnc(number);
//80
```

---

###### 9. shorthand

```javascript
// old ways
const cat = "Milo";
const dog = "Coco";
const someObject = {
  cat: cat,
  dog: dog,
};
```

```javascript
// es6
const cat = "Milo";
const dog = "Coco";
const someObject = {
  cat,
  dog,
};
```

---

###### 10. async await VS then catch

```javascript
// old ways

const greeting = new Promise((resolve, reject) => {
  resolve("Hello!");
});

greeting
  .then((value) => {
    console.log("The Promise is resolved!", value);
  })
  .catch((error) => {
    console.error("The Promise is rejected!", error);
  })
  .finally(() => {
    console.log("The Promise is settled, meaning it has been resolved or rejected.");
  });
```

```javascript
// new ways
// in async function you need to wrap your function in a try catch block
// never work in async function without this

async function doSomethingAsynchronous() {
  try {
    const value = await greeting;
    console.log("The Promise is resolved!", value);
  } catch((error) {
    console.error("The Promise is rejected!", error);
  } finally {
    console.log(
      "The Promise is settled, meaning it has been resolved or rejected."
    );
  }
}



```

```javascript
// when returning a Promise inside an async function,
// you don’t need to use await
async function getGreeting() {
  return greeting;
}
// you do need to write return await if you’re looking to handle
// the Promise being rejected in a try...catch block.
async function getGreeting() {
  try {
    return await greeting;
  } catch (e) {
    console.error(e);
  }
}
```

---

###### 11. using if

:x:

```javascript
if(
    type == 1 ||
    type == 2 ||
    type == 3 ||
    type == 4 ||
){
   //...
}
```

:white_check_mark:

```javascript
const condition = [1, 2, 3, 4];
if (condition.includes(type)) {
  //...
}
```

---

###### 12. using find instead of filter (optomization)

:x:

```javascript
const a = [1, 2, 3, 4, 5];
const result = a.filter((item) => {
  return item === 3;
});
```

:white_check_mark:

<!-- performance optimization: If a qualifying item is found in the find method,
it will not continue to traverse the array. -->

```javascript
const a = [1, 2, 3, 4, 5];
const result = a.find((item) => item === 3);
```

---

###### 13. non-empty judgment

:x:

```javascript
if (value !== null && value !== undefined && value !== "") {
  //...
}
```

:white_check_mark:

 <!-- use the new null value coalescing -->

```javascript
if ((value ?? "") !== "") {
  //...
}
```

---

###### 14. Conditionally add properties in a JavaScript Object

```javascript
const isValid = false;
const age = 18;
// we can use spread operator (...) to add properties in object
const person = {
  id: "adc",
  name: "mina",
  ...(isValid && { isActive: true }),
  ...(age >= 18 && { cart: 0 }),
};
// output { id: "adc", name: "mina", cart: 0}
```

---

###### 15. logical assignment operators p1

```javascript
// nullish coalescing asignment operator it will check whether
// or not a value is falsey and if it is , it will assign an other value to it
const stats = { speed: 50 };
stats.speed ??= 100;
console.log(stats.speed);
//output 50

stats.color ??= "white";
console.log(stats.color);
// output white
```

---

###### 16. logical assignment operators p2

```javascript
// OR & Equals (||=)
// old way
if (!user.id) {
  user.id = 1;
}
user.id = user.id || 1;

// new way
user.id ||= 1;
```

```javascript
// and & Equals (&&=)
// The logical AND assignment (x &&= y) operator only assigns if x is truthy.
// x &&= y is equivalent to x && (x = y);
let a = 1;
let b = 0;

a &&= 2;
console.log(a);
// expected output: 2

b &&= 2;
console.log(b);
// expected output: 0
```

---

###### 17. using Guard Clauses instead of if-else

:x:

```javascript
function getInsuranceDeductible(insurance) {
  if (insurance.covered) {
    if (insurance.majorRepair) {
      return 500;
    } else if (insurance.mediumRepair) {
      return 300;
    } else {
      return 100;
    }
  } else {
    return 0;
  }
}
```

:white_check_mark:

```javascript
function getInsuranceDeductible(insurance) {
  if (!insurance.covered) return 0;
  if (insurance.majorRepair) return 500;
  if (insurance.mediumRepair) return 300;

  return 100;
}
```

---
