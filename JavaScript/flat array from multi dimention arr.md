### How to flattern a multi-dimensional array
```javascript
let smileys = ['🥰', ['😄', '😃'], '😉', ['🥲', '😑']];
```

### We can use array.flat() method to flattern one level array
```javascript
console.log(smileys.flat()); // ['🥰', '😄', '😃', '😉', '🥲', '😑']
```

### Multi level array
```javascript
let smileys2 = ['🥰', ['😄', '😃', ['🥲', '😑']], '😉'];
```

### We can pass 'Infinity' parameter to array.flat function
```javascript
console.log(smileys2.flat(Infinity)); // ['🥰', '😄', '😃', '🥲', '😑', '😉']
```
