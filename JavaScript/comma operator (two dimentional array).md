### Comma operator.
comma operator allways return last value of operant of comma operator
```js
  let x = 1;
  x = (x++, x);
  console.log(x); // 2

  let y = (2, 3);
  console.log(y); // 3

  let a = [[1, 2, 3, 4], [3, 4, 5], [5, 6], [7]];

  for (let i = 0, j = 3; i <= 3; i++, j--) {
    console.log("a[" + i + "][" + j + "] = " + a[i][j]);  // run and check
  }
```
