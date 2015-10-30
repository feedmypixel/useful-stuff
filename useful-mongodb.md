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
db.createCollection(<collection_name>, [options])
```

#### Insert into collection
```
db.<collection>.insert(<document_or_array_of_documents>)
```

#### Drop database
```
use <database_name>
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

#### Formatted collection view
```
db.<collection>.find().pretty()
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