# 1. Delete Duplicates

```sql
WITH cte
AS
(
	select id, name, city, ROW_NUMBER() OVER (PARTITION BY name, city ORDER BY name, city) row_number
    FROM EMPLOYEE
)
DELETE FROM cte 
WHERE row_number > 1
```



# 2. MERGE Records

```sql
MERGE customers c
USING customers_temp ct
ON (c.ID = ct.ID)
WHEN MATCHED
	THEN 
		UPDATE SET c.name = ct.name

WHEN NOT MATCHED
	THEN
		INSERT VALUES ('Prajwal')
		
WHEN NOT MATCHED BY SOURCE
	THEN DELETE;
```



# 3. Pagination

```sql
SELECT *
FROM EMPLOYEES
ORDER BY COLUMN_NAME
OFFSET 10 ROWS
FETCH NEXT 10 ROWS ONLY

-- Get top 5 employees having max salary
SELECT *
FROM EMPLOYEES
ORDER BY SALARY DESC
OFFSET 0 ROWS
FETCH NEXT 5 ROWS ONLY

-- Get 3rd highest salary employee
SELECT *
FROM EMPLOYEES
ORDER BY SALARY DESC
OFFSET 2 ROWS
FETCH NEXT 1 ROWS ONLY
```

