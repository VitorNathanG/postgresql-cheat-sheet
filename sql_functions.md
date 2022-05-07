# Function samples

### Simple sum
```sql
CREATE OR REPLACE FUNCTION sum(int, int)
RETURNS int AS
$$
    SELECT $1 + $2
$$
LANGUAGE SQL;
```

### Weird Nested Select Thingy

```sql
CREATE OR REPLACE FUNCTION fn_biggest_order() 
RETURNS double precision AS -- This could be a view I guess
$$
    SELECT MAX(amount) FROM(
        SELECT order_id, SUM(unit_price * quantity) AS amount
        FROM order_details GROUP BY order_id
    ) AS total_amount
$$
LANGUAGE SQL;
```