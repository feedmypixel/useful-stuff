# Useful NPM Stuff

### Save npm install in dependencies
```
npm i <middleware> —-save-dev
```

### Clean npm cache clean (when having install problems)
```
npm cache clean
```

### Check and update dependencies in package.json
```
npm outdated
```

### npm-check-updates
```
npm install -g npm-check-updates
```

### Show versions of package on nom
```
npm view <package_name> versions 
```
### NPM Global libs location
```
/usr/local/lib/node_modules/
```

### List all locally installed modules
```
npm ls 
```

### Pre and Post task tasks
For any task you can use the `pre`<task> or `post`<task> syntax.

```json
"scripts": {
    "prelint": "perform task before linting",
    "lint": "perform linting task",
    "postlint": "perform task after linting",
}
```