# pg size

## database size with index
```
select pg_size_pretty(pg_total_size('mydb'));
```

## database size without index
```
select pg_size_pretty(pg_database_size('mydb'));
```

## index size
```
select pg_size_pretty(pg_indexes_size('mytable'));
```

## table size with index
```
select pg_size_pretty(pg_total_relation_size('mytable'));
```

## table size without index
```
select pg_size_pretty(pg_relation_size('mytable'));
```

## tablespace size
```
select pg_size_pretty(pg_tablespace_size('pg_global'));
```

## table file path
```
select pg_relation_filepath('mytable');
```

## switch log
```
select pg_switch_xlog();
```

## switch next log file
```
select pg_rotate_logfile();
```

## reference
```
select
	table_name,
	pg_size_pretty(table_size) as table_size,
	pg_size_pretty(indexes_size) as indexes_size,
	pg_size_pretty(total_size) as total_size
from
	(
	select
		table_name,
		pg_table_size(table_name) as table_size,
		pg_indexes_size(table_name) as indexes_size,
		pg_total_relation_size(table_name) as total_size
	from
		(
		select
			('"' || table_schema || '"."' || table_name || '"') as table_name
		from
			information_schema.tables
) as all_tables
	order by
		total_size desc
) as pretty_sizes;
```