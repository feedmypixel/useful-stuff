# Useful Concourse Stuff

#### Setup a login

```
$ fly --target <target> login --team-name my-team --concourse-url https://ci.example.com
```

#### Login with target
```
fly -t <target>
```

#### show targets
```
fly targets
```

#### List resource types
```
fly -t example workers -d
```

#### Have a look at the build machine
```
fly -t <target> intercept
```

#### Delete pipeline
```
fly -t <target> destroy-pipeline -p <pipeline-name>
```

#### Deploy pipeline
```
fly -t <target> set-pipeline -p <pipeline> -c <config>
```
###### example:

```
fly -t fpdp set-pipeline --pipeline benc-fesk-pdp --config ci/pipeline.yml
```

#### Trigger Job
```
fly -t fs trigger-job -j <pipeline>/<job>
```

#### Trigger job (with watch)
```
fly -t <target> trigger-job --job <pipeline>/<job> --watch
```



