# Useful Node.js Stuff

### Table of contents
- [Env](#env)
- [Inspector](#inspector)
- [Run](#run)

<a name="env">
## Env

#### Switch node environment
```
NODE_ENV=development node app.js
```

#### Switch node environment (using nodemon)
```
NODE_ENV=development nodemon app.js
```


<a name="inspector">
## Node inspector

#### Debug node inspector
To use node-inspector, enable debugging on the node you wish to debug. You can either start node with a debug flag like:

```
node --debug your/node/program.js
```

#### Start node inspector 
```
node-inspector &
```

<a name="run">
## Run

#### Run program in background
```
program name &
```

#### Send job to foreground
```
fg [pid]
```

#### Print out result in cli
```
node -pe "require('url').parse('/test?q=1', true)"
```