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

## Comparison operators
| Operator     | Description           |   |
| --------     | -----------           |   |
| `<`          | less than             |   |
| `>`          | greater than          |   |
| `<=`         | less than or equal    |   |
| `>=`         | greater than or equal |   |
| `=`          | equal                 |   |
| `<>` or `!=` | not equal             |   |


## Queries
- Select and skip duplicates
```sql
SELECT DISTINCT field FROM table;
```

- Select with condition
```sql
SELECT * FROM table WHERE gender = 'female';
SELECT * FROM table WHERE gender = 'male' AND name = 'John';
SELECT * FROM table WHERE gender = 'male' AND (name = 'John' OR name = 'Jake');
```

- Offset and limit
```sql
SELECT * FROM table LIMIT 10; 
SELECT * FROM table OFFSET 10 LIMIT 10;
```

- Range
```sql
SELECT * FROM table WHERE country_of_birth IN ('Russia', 'Korea', 'Australia');
```

- Between
```sql
SELECT * FROM table WHERE date_of_birth BETWEEN DATE '1998-01-01' AND '2009-01-01';
```

- Like
```sql
SELECT * FROM table WHERE email LIKE '%@gmail.com';
SELECT * FROM table WHERE email LIKE '%@gmail.%';
SELECT * FROM table WHERE email LIKE '______@%';
-- Ignore case
SELECT * FROM table WHERE email ILIKE '%@Gmail.%';
```

- Group
```sql
SELECT first_name, COUNT(*) FROM table GROUP BY first_name ORDER BY count DESC;
SELECT first_name, COUNT(*) FROM table GROUP BY first_name HAVING COUNT(*) > 2 ORDER BY count DESC;
```

- Aggregate functions
```sql
SELECT first_name, COUNT(*) FROM table GROUP BY first_name ORDER BY count DESC;
SELECT first_name, COUNT(*) FROM table GROUP BY first_name HAVING COUNT(*) > 2 ORDER BY count DESC;
```

