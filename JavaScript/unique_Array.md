__If we want to Make an Unique Array from a Normal Array__

then: ``` make this array to set() and make array again```

Ex:
```
var a = [1,2,3,2,1,4,3,4,5,7,8,6]
console.log([...new Set(a)]);
```
result: 
``` 
[
  1, 2, 3, 4,
  5, 7, 8, 6
]
```
