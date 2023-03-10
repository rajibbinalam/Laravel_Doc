### ```This``` confussion avoid by ARROW Function. () => {}


### #Vanila JS
```js
const javascript = {
  name: 'Javascript',
  libraries: ['React', 'Vue', 'JQuery'],
  printLibraries: function() {
    this.libraries.forEach(function(library){
      console.log(`${this.name} Loves ${library}`);
    }.bind(this))       // if you want to use 'this' of 'javascript' object. You Should bind(this)
  }
}
```
###### OR
```js
const javascript = {
  name: 'Javascript',
  libraries: ['React', 'Vue', 'JQuery'],
  printLibraries: function() {
    let self = this;
    this.libraries.forEach(function(library){
      console.log(`${self.name} Loves ${library}`);
    })
  }
}
```

### #JS ES6 / Arrow Function
##### Arrow fn automatically get parent 'this' as own 'this'. Do not need bind
```js
const javascript = {
  name: 'Javascript',
  libraries: ['React', 'Vue', 'JQuery'],
  printLibraries: function() {
    this.libraries.forEach((library) => {
      console.log(`${this.name} Loves ${library}`);
    })
  }
}
```
