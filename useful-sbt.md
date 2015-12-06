# Useful SBT Stuff

#### Commands in sbt scala console 
> type help to see full list

- clean
- compile
- reload
- update
- projects
- project
- run
- test

#### Run with port
```
sbt
```
```
run <port_number>
```

#### Run with port shortcut
```
sbt '~run 9020'
```

#### Add a watcher on scala tests
```
sbt ~test
```

#### Add a watcher on publish-local
```
sbt ~publish-local
```

#### To return to cli
```
ctrl d
```

#### If you want to run particular suites, use test-only and provide their fully qualified names in a space separated list
```
test-only org.acme.RedSuite org.acme.BlueSuite
```

#### Or you can specify a glob
```
test-only *RedSuite
```

#### A glob with watcher
```
~test-only *RedSuite
```