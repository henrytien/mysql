## Basics 

### Select 

```mysql
SELECT
  first_name,
  last_name,
  points,
  (points + 10) * 100 AS 'discount factor'
FROM customers;
```



```mysql
SELECT
distinct state
FROM customers;
```

Output :

```
'VA'
'CO'
'FL'
'TX'
'IL'
'TN'
'CA'
'GA'
```

```mysql
SELECT
*
FROM customers
WHERE birth_date > '1990-01-08'OR 
(points > 1000 AND state = 'VA');

SELECT
*
FROM customers
WHERE NOT (birth_date > '1990-01-08'
OR points > 1000)
```

### ike

```mysql
SELECT * 
FROM customers
WHERE last_name LIKE 'B____y'
```

% any number of characters

_ single character

### Regexp

```mysql
SELECT * 
FROM customers
WHERE last_name REGEXP 'field$'
```



```mysql
SELECT * 
FROM customers
WHERE last_name REGEXP '[a-h]e'
```

^ begining

$ end

| logical or

[abcd] 

[a-d] range

### NULL

```mysql
SELECT * 
FROM customers
WHERE phone IS NOT NULL
```

### ORDER BY

```mysql
SELECT * 
FROM customers
ORDER BY state, first_name DESC
```

```mysql
SELECT first_name, last_name
FROM customers
ORDER BY 1, 2
```

```mysql
SELECT * , quantity * unit_price AS total_price
FROM order_items
ORDER BY total_price DESC 
```

### LIMIT

```mysql
SELECT * 
FROM customers
LIMIT 0, 3
```

### INNER JOINS

```mysql
SELECT order_id, o.customer_id,first_name
FROM orders o   
JOIN customers c ON o.customer_id = c.customer_id
```

### Joining Across Databases

```mysql
SELECT * 
FROM order_items oi
JOIN sql_inventory.products p 
ON oi.product_id = p.product_id
```

