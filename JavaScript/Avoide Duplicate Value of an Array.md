### Avoide Duplocate Value of an Array.
```js
        const arr = [1,1,2,3,4,5,6,7,8,5,8,9,3,5,9,10];
        const nArr = [...new Set(arr)]
        console.log(nArr);
```
