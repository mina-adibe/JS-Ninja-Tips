###### 1. await - promise.all

```javascript
const user = await getUser();
const product = await getProducts();
```

> Up to twice as faster

```javascript
const [user, products] = await Promise.all([getUser(), getProducts()]);
```
