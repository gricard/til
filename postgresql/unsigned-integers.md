# Unsigned Integers in PostgreSQL tables

The SQL standard does not define unsigned integers, so pgsql does not implement it (unlike MySQL, which I grew up using).
In pgsql, this is how you define a column as an unsigned integer:

```sql
CREATE TABLE my_table (
    id SERIAL PRIMARY KEY,
    num INTEGER CHECK (num >= 0)
);
```