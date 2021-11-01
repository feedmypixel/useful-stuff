# Useful Google Cloud Platform Stuff

#### Logs
Logs explorer add a query to see the url
```
httpRequest.requestUrl="<url>"
```

#### Log queries
Various ways of searching for something
```
=           # equal
!=          # not equal
> < >= <=   # numeric ordering
:           # "has" matches any substring in the log entry field
=~          # regular expression search for a pattern
!~          # regular expression search not for a pattern
```

#### Negate a query
Negate a query by placing a `-` infront of the query
```
-httpRequest.requestUrl=~"something-we-want-to-find"
```

#### Find all 4xx
```
httpRequest.status>399 httpRequest.status<500
```

#### Finding services
When clicking into a query you can use the "Resource" button to select your service

#### Latency
You can click on the latency in the logs and select a condition to show the logs, "greater than", "less than"



## CLI

#### Login (use this to login)
```
gcloud auth application-default login
```

#### Print auth token
```
gcloud auth print-identity-token
```

#### Switch acount
```
gcloud config set account <email>
```

#### List current project
```
gcloud config list
```

#### List projects
```
gcloud projects list
```

### Create configuration
```
gcloud config configurations create <name>
```

### Init configuration
```
gcloud init
```

### List configurations
```
gcloud config configurations list
```

### Activate (select) configurations
```
gcloud config configurations activate <name>
```

### List services
```
gcloud run services list --platform managed
```

### Remove services
```
gcloud run services delete <name>
```

### Get current CloudRun version
```
gcloud run services describe web --region europe-west1 | head -10
```

### Get docker registry versions
```
gcloud container images list-tags eu.gcr.io/pretamanger-web-lab/web | head -5
```

