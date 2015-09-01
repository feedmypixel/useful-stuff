# Useful SBT Stuff

### Commands in sbt scala console 
> type help to see full list

- clean
- compile
- reload
- update
- projects
- project
- run
- test

### Add a watcher on scala tests
```
~test
```

### To return to cli
```
ctrl d
```

### If you want to run particular suites, use test-only and provide their fully qualified names in a space separated list
```
test-only org.acme.RedSuite org.acme.BlueSuite
```

### Or you can specify a glob
```
test-only *RedSuite
```