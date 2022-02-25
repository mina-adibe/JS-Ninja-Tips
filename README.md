###### 1. await - promise.all

```javascript
const user = await getUser();
const product = await getProducts();
```

```javascript
const [user, products] = await Promise.all([getUser(), getProducts()]);
```
