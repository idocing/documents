# pg

## row number
```sql
SELECT ROW_NUMBER() OVER (PARTITION BY id ORDER BY id) AS rid, *
FROM user u;
```