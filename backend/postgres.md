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

- Start/stop postgres on Ubuntu
```sh
sudo service postgresql start
sudo service postgresql stop 
```

- Create db from file
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

## Frequently used commands in psql mode
```sh
# list roles
\du

# list tables
\dt

# list dbs
\l

# describe table, view, sequence
\d table_name

# connect to db
\c db_name

# list of functions
\df

# list of extensions
\dx

# expanded display
\x

# quit
\q
```


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
-- count
SELECT first_name, COUNT(*) FROM table GROUP BY first_name ORDER BY count DESC;
SELECT first_name, COUNT(*) FROM table GROUP BY first_name HAVING COUNT(*) > 2 ORDER BY count DESC;
-- max, min, avg
SELECT MAX(price) FROM car;
SELECT MIN(price) FROM car;
SELECT AVG(price) FROM car;
-- round result
SELECT ROUND(AVG(price)) FROM car;
-- sum
SELECT SUM(price) FROM car;
SELECT make, SUM(price) FROM car GROUP BY make;
```

- Basic arithmetic
```sql
-- show rounded car price and 10% of the price and car price minus 10%
SELECT *, ROUND(price * .10, 2), ROUND(price - (price * .10), 2) FROM car;
-- same with aliases
SELECT *, ROUND(price * .10, 2) AS ten_percent, ROUND(price - (price * .10), 2) AS sale_price FROM car;
```

- Coalesce
```sql
-- ignore null values or substitute them with provided value
SELECT COALESCE(email, 'no email') FROM person;
```

- Extensions 
```sql

-- list installed extensions
SELECT * FROM pg_extension;

-- list available extensions
SELECT * FROM pg_available_extensions;

-- uuid
CREATE EXTENSION IF NOT EXISTS "uuid-ossp";

```

- Insert with unique id
```sql
INSERT INTO person(id, name) values (uuid_generate_v1(), 'John', 'Snow');
```

- Null
```sql
SELECT COALESCE(10 / NULLIF(0, 0), 0);
```

- Timestamps
```sql
SELECT NOW();
SELECT NOW()::DATA;
SELECT NOW()::TIME;
```

- Arithmetic with dates
```sql
SELECT NOW() - INTERVAL '1 YEAR';
SELECT NOW() - INTERVAL '10 MONTHS';
SELECT NOW() + INTERVAL '100 DAYS';
SELECT (NOW() + INTERVAL '100 DAYS')::DATE;
```

- Extract part of a date
```sql
SELECT EXTRACT(YEAR FROM NOW());
```

- Age function
```sql
SELECT *, AGE(NOW(), date_of_birth) AS age FROM person;
```

- Remove primary key constraint
```sql
ALTER TABLE person DROP CONSTRAINT person_pkey;
```

- Add primary key
```sql
DELETE FROM person WHERE id = 1;
ALTER TABLE person ADD PRIMARY KEY (id);
```

- Add/remove unique constraint
```sql
ALTER TABLE person ADD CONSTRAINT unique_email UNIQUE (email);
ALTER TABLE person ADD UNIQUE (email);
ALTER TABLE person DROP CONSTRAINT unique_email; 
```

- Check constraints
```sql
ALTER TABLE person ADD CONSTRAINT check_gender CHECK (gender = 'Female' OR gender = 'Male');
```

- Delete
```sql 
DELETE FROM person WHERE id = 12;
```

- Update
```sql
UPDATE person SET name = 'test', email = 'test@test.com' WHERE id = 12;
```

- Conflict
```sql
INSERT INTO person (id, name, email) VALUES (11, 'Chandler', 'bing@bing.com') ON CONFLICT (id) DO NOTHING;
INSERT INTO person (id, name, email) VALUES (11, 'Chandler', 'bing@bing.com') ON CONFLICT (id) DO UPDATE SET name = EXCLUDED.name, email = EXCLUDED.email;
```

- Relations
```sql

CREATE TABLE customers (
    id BIGSERIAL NOT NULL PRIMARY KEY,
    email VARCHAR(100) NOT NULL,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    date_of_birth DATE NOT NULL,
    country VARCHAR(50) NOT NULL,
    phone_number VARCHAR(50),
    address TEXT,
    UNIQUE(email)
);

CREATE TABLE orders (
    id BIGSERIAL NOT NULL PRIMARY KEY,
    brand VARCHAR(100) NOT NULL,
    category VARCHAR(100) NOT NULL,
    customer_id BIGINT REFERENCES customers (id),
    UNIQUE(customer_id)
)

```

- Update foreign keys
```sql
UPDATE orders SET customer_id = 3 WHERE id = 1;
```

- Inner joins
```sql
SELECT * FROM orders JOIN customers ON orders.customer_id = customers.id;
SELECT * FROM orders JOIN customers USING (customer_uid);
```

- Left joins
```sql
SELECT * FROM orders LEFT JOIN customers ON orders.customer_id = customers.id;
SELECT * FROM orders LEFT JOIN customers ON orders.customer_id = customers.id WHERE customers.* IS NULL;
```

- Export to csv 
```sh
\copy (SELECT * FROM orders LEFT JOIN customers ON orders.customer_id = customers.id) TO '~/Documents/orders.csv' DELIMITER ',' CSV HEADER;
```

- Serial and sequences
```sql
SELECT * FROM orders_id_seq;
ALTER SEQUENCE orders_id_seq RESTART WITH 5;
```

- UUID
```sql

CREATE TABLE customers (
    customer_uid UUID NOT NULL PRIMARY KEY,
    email VARCHAR(100) NOT NULL,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    date_of_birth DATE NOT NULL,
    country VARCHAR(50) NOT NULL,
    phone_number VARCHAR(50),
    address TEXT,
    UNIQUE(email)
);

CREATE TABLE orders (
    order_uid UUID NOT NULL PRIMARY KEY,
    brand VARCHAR(100) NOT NULL,
    category VARCHAR(100) NOT NULL,
    customer_uid UUID REFERENCES customers (order_uid),
    UNIQUE(customer_uid)
)

INSERT INTO orders (order_uid, brand, category) VALUES (uuid_generate_v4(), 'Dior', 'creme', 'aging');

```
