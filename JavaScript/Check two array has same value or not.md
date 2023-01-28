### Check two array has same value or not.
<p>if we have two array a=[1,2] and b=[2,3]. Check a and b is same array or not<p/>
<p>compare two arrays by value</p>

```js
const hasSameElements = (a, b) => {
  return a.length === b.length && a.every((v, i) => v === b[i]);
};

console.log(hasSameElements([1, 2], [1, 2]));
```
