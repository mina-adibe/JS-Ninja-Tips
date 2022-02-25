###### 1. await - promise.all

[//]: # "don't"

```javascript
const user = await getUser();
const product = await getProducts();
```

[//]: # "Up to twice as fasr"
[//]: # "do"

```javascript
const [user, products] = await Promise.all([getUser(), getProducts()]);
```
