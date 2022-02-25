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
