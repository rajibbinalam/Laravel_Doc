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