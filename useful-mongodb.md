# Useful MongoDB Stuff

#### Start MongoDB
```
mongod
```

#### Connect to a mongod
```
mongo
```

#### Show databases
```
show dbs
```

#### Switch to a new database or create database
```
use <database_name>
```

#### Create collection
```
db.createCollection(<collection name>, [options])
```

#### Drop database
```
use <db name>
db.dropDatabase()
```

#### Show collections
```
show collections
```

#### Show contents of collection 
```
db.<collection>.find({})
```

#### Help
```
help
```

#### Start mongos with a specific conf
```
mongod --config /etc/mongodb/mongo.conf
```

#### Switch to admin db
```
use admin
```

#### Auth as user
```
db.auth('author', 'pass');
```

#### Add admin user
```
db.addUser({user: 'author', pwd: 'pass', roles: ['readWriteAnyDatabase', 'clusterAdmin', 'userAdmin', 'userAdminAnyDatabase']})
```

#### Add read write user
```
db.addUser( { user: 'author', pwd: 'pass', roles: [ 'readWrite' ] } )
```

#### Remove user
```
db.removeUser('username');
```