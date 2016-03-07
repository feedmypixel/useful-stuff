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

#### Quick test (just failing tests)
```
sbt test-quick
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
```
testOnly controllers.SecureLoginControllerSpec
```

#### Or you can specify a glob
```
test-only *RedSuite
```

#### with glob and test with the word 'redirect' in it
```
test-only *Challenge* -- -z redirect
```

#### with glob in sbt
```
sbt
```
```
testOnly *SecureLogin*
```

#### It tests
```
sbt "it:test-only controllers.SecureLoginControllerWithSecureFormEnabledISpec"
```

Or, if you are in the sbt console you don't need quotes
```
it:test-only controllers.SecureLoginControllerWithSecureFormEnabledISpec
```

#### A glob with watcher
```
~test-only *RedSuite
```