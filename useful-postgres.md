# Useful Postgres

#### Connect to PostGres container bash
```
docker exec -it <container_name> bash
```

#### Change to user ‘postgres’

```
su postgres
```

#### PostGres cli
```
psql
```

#### Connection info
```
\conninfo
```

#### Quit
```
\q
```

#### List databases
```
\l
```

#### Connect to database
```
\c <database_name>
```

#### List schemas
```
\dt
```

#### List tables
```
\dt
```

#### Describe table
```
\d <table_name>
```

## DataBase work

#### Create Table
```
CREATE TABLE IF NOT EXISTS plants (
	plant_id serial PRIMARY KEY,
	name VARCHAR ( 50 ) UNIQUE NOT NULL,
	created_on TIMESTAMP NOT NULL
);
```

#### Insert
```
INSERT INTO plants(name, created_on) 
VALUES('Cactus', CURRENT_TIMESTAMP);
```

#### Select
```
SELECT * FROM plants;
```

## Dump/restore
To restore a DB into docker locally use
```
docker exec -i <docker-image-name> psql -U postgres -v -d <db_name> < /db_dump.sql
```







