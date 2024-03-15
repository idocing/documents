# uuid

## postgres uuid
```
CREATE EXTENSION "uuid-ossp";

CREATE TABLE IF NOT EXISTS user_info (
    id uuid DEFAULT uuid_generate_v4(),
    username varchar(100),
    nickname varchar(100)
);

INSERT INTO user_info (username, nickname) VALUES 
('zhangsan', '张三');
```
