# Useful Cloudfoundry stuff

### Table of contents
- [Logs](#logs)
- [App](#app)
- [Logout](#logout)
- [Visability](#visability)
- [SSH](#ssh)
- [Push](#push)


## Target
Target an Org
```
cf target -o <org-name>
```

Target a space
```
cf target -s <space-name>
```

## Logs
View logs
```
cf logs <app-name>
```

With backtrace
```
cf logs <app-name> --latest
``` 

## App
See app info
```
cf app <app-name>
```

## Logout
```
cf logout
```

## Visability
Shows all the top level organisations you're allowed to see
```
cf orgs
``` 

Shows you which ‘spaces’ those are separated into
```
cf spaces
```

Physical info on the apps running in your space
```
cf apps
```

## SSH
Logs you in to an app 
```
cf ssh <app-name>
``` 

## Push
Pushes an app without
```
cf push <app>
```

