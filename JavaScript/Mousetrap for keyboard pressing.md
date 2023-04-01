### Key Board Pressing and Handling events
### We'll use MouseTrap Library for KeyPressing Events

#### JS files
```js
// CDN
<script src="https://craig.global.ssl.fastly.net/js/mousetrap/mousetrap.min.js"></script>
```
#### Simple two Functions:
```js
//  Single Key Events
Mousetrap.bind('ctrl+shift+m', function() {
    alert('You pressed the Ctrl+Shift+M key combination!');
});

//  Multiple Key Events
Mousetrap.bind(['ctrl+shift+m', 'ctrl+s', 'pageup'], function() {
    alert('You pressed the Ctrl+Shift+M / ctrl+s / pageup key combination!');
});
```

[For More OR See The Doc](https://craig.is/killing/mice)
