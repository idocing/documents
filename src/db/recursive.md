# recursive

## ddl
```
create table if not exists dept (
    id bigint,
    name varchar,
    pid bigint default 0,
    level int default 1
)
```

## dml
```
insert into dept values
(1, 'dept1', 0, 1),
(2, 'dept2', 0, 1),
(3, 'dept11', 1, 2),
(4, 'dept21', 2, 2),
(5, 'dept111', 3, 3),
(6, 'dept211', 4, 3),
(7, 'dept1111', 5, 4),
(8, 'dept2111', 6, 4),
(9, 'dept11111', 7, 5);
```

## downward
```
with recursive
dd as (
    select d1.id, d1.pid, d1.name, d1.level
    from dept d1
    where d1.name = 'dept2'
    union
    select d2.id, d2.pid, d2.name, d2.level
    from dept d2
    join dd
    on d2.pid = dd.id
)
select id, pid, name, level from dd;
```

## upward
```
with recursive
dd as (
    select d1.id, d1.pid, d1.name, d1.level
    from dept d1
    where d1.name = 'dept11111'
    union
    select d2.id, d2.pid, d2.name, d2.level
    from dept d2
    join dd
    on d2.id = dd.pid
)
select id, pid, name, level from dd;
```