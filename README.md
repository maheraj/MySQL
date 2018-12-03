# MySQL
## Querying Data
* Select
* Select Distinct

## Filtering Data
* Where
* AND
* OR
* IN
* BETWEEN
```
SELECT 
    productCode, 
    productName, 
    buyPrice
FROM
    products
WHERE
    buyPrice BETWEEN 90 AND 100;

```
* LIKE
* LIMIT
* IS NULL

## Sorting Data
* ORDER BY
* Natural sorting using ORDER BY clause

## Joining Tables
* alias
* CROSS JOIN
* INNER JOIN
* LEFT JOIN
* RIGHT JOIN

## GOUPING DATA
* GROUP BY
* HAVING
* ROLLUP

## STORE PROCEDURE
```
DELIMITER //
CREATE PROCEDURE GetAllProducts()
BEGIN
SELECT * FROM products;
END//
DELIMETER ;
```

## TRIGGER

```
DELIMITER $$
CREATE TRIGGER before_employee_update
    BEFORE UPDATE ON employee
    FOR EACH ROW
BEGIN
    INSERT INTO employee_audit
    SET action = 'update'
    employeeNumber = OLD.employeeNumber,
    lastName = OLD.lastName,
    changedat = NOW();
END$$
DELIMITER ;


```

## MYSQL View
In SQL, a view is a virtual table based on the result-set of an SQL statement. A view contains rows and columns, just like a real table. The fields in a view are fields from one or more real tables in the database.

```
CREATE VIEW view_salePerOrder AS
    SELECT orderNumber, SUM(quantity * priceEach) total
    FROM
        orderDetails
    GROUP BY orderNumber
    ORDER BY total DESC;
    
```
