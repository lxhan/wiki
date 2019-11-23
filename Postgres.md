# Postgresql

## Create 
- Init db
```sh
adduser postgres
mkdir /usr/local/pgsql/data
chown postgres /usr/local/pgsql/data
su - postgres
initdb -D /usr/local/pgsql/data
pg_ctl -D /usr/local/pgsql/data -l logfile start
createdb test
psql test
```

- Init db from file
```sh
psql
\i /path/to/db/file.sql
```

## Connect
```sh
psql -h localhost -p 5432 -U user db
```


## Queries
- Select and skip duplicates
```sql
SELECT DISTINCT field FROM table;
```
