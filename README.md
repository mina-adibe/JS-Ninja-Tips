###### 1. await - promise.all

[//]: # "don't"

```javascript
const user = await getUser();
const product = await getProducts();
```

<!--- Up to twice as faster --->

[//]: # "Up to twice as faster"
[//]: # "do"

```javascript
const [user, products] = await Promise.all([getUser(), getProducts()]);
```
