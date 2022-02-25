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
