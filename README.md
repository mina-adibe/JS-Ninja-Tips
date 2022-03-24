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
