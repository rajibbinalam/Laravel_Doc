### Click a button to copy selected text.

```html
    <input type="text" name="" value="Hello Test" id="inputText">
    <button onclick="copyTextFn()">Copy</button>
```
```js
        function copyTextFn(){
            $('#inputText').select();
            document.execCommand('copy');  // Pest Any where => Hello Test
        }
```
