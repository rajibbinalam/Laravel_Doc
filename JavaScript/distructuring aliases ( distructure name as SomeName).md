### Distructuring an Object name as SomeThinkName. its called Distructuring Aliases
  <p>if we have so many name variables then it's dificult to dictructure name. Cause name will duplicate or replace with others.. saw the Example</p>

```js
        const language = {
            name: 'JS',
            founded: 1996,
            founder: "Eich"
        }
        const {name: langName, founded: lnagFounded} = language;
        console.log(langName, lnagFounded);
```
