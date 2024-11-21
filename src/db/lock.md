# lock

## optimistic lock
```
create table if not exists users (
    id bigserial primary key,
    name varchar not null,
    version int not null default 0
);

insert into users (name) values ('zhangsan'), ('lisi');
```

```
update users
set name = 'wangwu', version = version + 1
where id = 1 and version = 0;
```