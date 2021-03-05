# Useful Google Cloud Platform Stuff

#### Logs
Logs explorer add a query to see the url
```
httpRequest.requestUrl="<url>"
```

#### Login (use this to login)
```
gcloud auth application-default login
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
