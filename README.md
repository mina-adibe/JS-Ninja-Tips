###### 1. await - promise.all

```javascript
const user = await getUser();
const product = await getProducts();
```

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
