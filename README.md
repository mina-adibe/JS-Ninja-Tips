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

###### 3. use Object.entries to access both key and value

:x:

```javascript
Object.keys(obj).forEach((key) => {
  const value = obj[key];
  // log out "key" and "value"
  console.log(key, value);
});
```

:white_check_mark:

```javascript
Object.entries(obj).forEach(([key, value]) => {
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
const es6 = Math.trunc(number);
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

###### 18. destructuring is slow

:x:

```javascript
const numbers = [10, 20, 30, 40, 50];

numbers.reduce((arr, v) => [...arr, v * 100], []);
```

:white_check_mark:

```javascript
numbers.reduce((arr, v) => {
  arr.push(v * 100);
  return arr;
}, []);
```

## <!-- another example  -->

:x:

```javascript
const people = [
  { id: 1, name: "Jack" },
  { id: 2, name: "Sally" },
  { id: 3, name: "Joe" },
];

people.reduce(
  (lookup, person) => ({
    ...lookup,
    [person.id]: person,
  }),
  {}
);
// javascript is actually going and creating a new object using Object.assign
// every single pass throught this reduce - o(n)cubed
// it will be in  es2015 (check it with TSplayground ):
people.reduce(
  (lookup, person) => Object.assign(Object.assign({}, lookup), { [person.id]: person }),
  {}
);
```

:white_check_mark:

```javascript
people.reduce((lookup, person) => {
  lookup[person.id] = person;
  return lookup;
}, {});
```

---

###### 19. bitwise operators with `.splice` method

:x:

```javascript
let list = [1, 2, 3, 4, 5];
// `indexOf` here will return -1, and therefore the `.splice` method remove the last item that is `5`
list.splice(list.indexOf(6), 1); // [1, 2, 3, 4]
```

:white_check_mark:

```javascript
let list = [1, 2, 3, 4, 5];
/*
  `indexOf` here will return -1 again, but in this time `>>>` ( Unsigned Right Shift Operator ) will convert `-1` to `4294967295` by shifting its bits
  and therefore the `.splice` method will try to remove the number in the index `4294967295` that is not exist :sunglasses:.
*/
list.splice(list.indexOf(6) >>> 0, 1);
```

---

###### 20. using `.at()` method

:x:

```javascript
const list = [1, 2, 3, 4, 5];
list[list.length - 1]; // 5
list[list.length - 2]; // 4
```

:white_check_mark:

```javascript
const list = [1, 2, 3, 4, 5];
list.at(-1); // 5
list.at(-2); // 4
```

###### 21. JavaScript URL API

```javascript
const url = new URL(
  "https://user:pass@daily-dev-tips.com:3000/folder/page?param=xyz&new=true#title2"
);

const { origin, pathname, search, hostname } = url;

//hostname :"daily-dev-tips.com"
// origin :'https://daily-dev-tips.com:3000'
// pathname : '/folder/page'
// search : '?param=xyz&new=true's

url.hash = "title4";
url.pathname = "register";

console.log(url.searchParams.get("param"));
// xyz

console.log(url.searchParams.get("new"));
// true

console.log(url.searchParams.getAll("param"));
// ["xyz"]

console.log(url.searchParams.has("param"));
// true

const keys = url.searchParams.keys();

const values = url.searchParams.values();
for (let value of values) {
  console.log(value);
}
// xyz
// true

url.searchParams.append("search", "JavaScript");
// search: "?param=xyz&new=true&search=JavaScript"

// try : set - remove - sort
```

---
