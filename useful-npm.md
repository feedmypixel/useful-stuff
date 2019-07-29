# Useful NPM Stuff

#### Update version
```
npm version <semver-version-number>
```

#### Publish
```
npm publish
```

#### View package details
```
npm view <pacakge-name>
```

#### Save npm install in dependencies
```
npm i <middleware> —-save-dev
```

#### Clean npm cache clean (when having install problems)
```
npm cache clean
```

#### Check and update dependencies in package.json
```
npm outdated
```

#### npm-check-updates
```
npm install -g npm-check-updates
```

#### Look for updates
```
ncu
```

#### Update package.json
```
ncu -u
```

#### Show versions of package on npm
```
npm view <package_name> versions 
```
#### NPM Global libs location
```
/usr/local/lib/node_modules/
```

#### List all locally installed modules
```
npm ls 
```

#### link
cd to dependecny repo you wish to link to

```
npm link
```

cd to repo you wish to link the dependency to (your app) the linked repo will be syminked in node_modules
```
npm link <package-name>
```

#### Pre and Post task tasks
For any task you can use the `pre`<task> or `post`<task> syntax.

```json
"scripts": {
    "prelint": "perform task before linting",
    "lint": "perform linting task",
    "postlint": "perform task after linting",
}
```

#### Reference a private github repo and branch
```
    "dependencies": {
        "fs-extra": "git+https://<github-dev-token>:x-oauth-basic@github.com/<user_name>/<repo>.git#<branch>"
```


#### Reference a github repo and branch
```
    "dependencies": {
        "fs-extra": "<user_name>/<repo>.git#<branch>"
```