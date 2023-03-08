### Install Dev Dependencies
```sh
    yarn add -D prettier
    yarn add -D babel-eslint
    npx install-peerdeps --dev eslint-config-airbnb
    yarn add -D eslint-config-prettier eslint-plugin-prettier
```
or You can also add a new script in the scripts section like below to install everything with a single command:
```json
scripts: {
    "lint": "yarn add -D prettier && yarn add -D babel-eslint && npx install-peerdeps --dev eslint-config-airbnb && yarn add -D eslint-config-prettier eslint-plugin-prettier"
}
```
and then simply run the below command in the terminal -
```sh
    yarn lint #or 'npm run lint'
```

### VS code workspace setting for react project

```json
{
  // Theme
  "workbench.colorTheme": "Dracula",

  // config related to code formatting
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.formatOnSave": true,
  "[javascript]": {
    "editor.formatOnSave": false,
    "editor.defaultFormatter": null
  },
  "[javascriptreact]": {
    "editor.formatOnSave": false,
    "editor.defaultFormatter": null
  },
  "javascript.validate.enable": false, //disable all built-in syntax checking
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true,
    "source.fixAll.tslint": true,
    "source.organizeImports": true
  },
  "eslint.alwaysShowStatus": true,
  // emmet
  "emmet.triggerExpansionOnTab": true,
  "emmet.includeLanguages": {
    "javascript": "javascriptreact"
  }
}
```




### If Having Error when Start => Follow [Go](https://www.youtube.com/watch?v=-oGMwOOHFyk&list=PLHiZ4m8vCp9M6HVQv7a36cp8LKzyHIePr&index=4)
