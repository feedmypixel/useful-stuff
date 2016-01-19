# Useful Heroku Stuff

#### Add heroku app as git remote
```
cd to <repository>
``` 
```
heroku git:remote -a <heroku_app>
```

#### Add another heroku app as a different remote
```
heroku git:remote -r <git_remote_name> -a <heroku_app>
```

#### Tail logs
```
heroku logs --tail
```
```
heroku logs --app <app_name> --tail
```

#### Help
```
heroku ps --help
```

#### Process
```
heroku ps --app <app_name>
```

#### Restart
```
heroku restart --app <app_name>
```
