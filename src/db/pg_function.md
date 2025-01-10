# pg function

## do for loop
```sql
DO 
$$
DECLARE 
r RECORD;
BEGIN
    FOR r IN (SELECT * FROM xxx) LOOP
    RAISE NOTICE 'row:%', r;
    END LOOP;
END;
$$;
```

## function
```sql
CREATE OR REPLACE FUNCTION test()
RETURNS void
AS
$$
DECLARE
r RECORD;
BEGIN 
    FOR r IN (SELECT * FROM xxx) LOOP
    RAISE NOTICE 'row:%', r;
    END LOOP;
END;
$$
LANGUAGE plpgsql;
SELECT test() AS output;
```