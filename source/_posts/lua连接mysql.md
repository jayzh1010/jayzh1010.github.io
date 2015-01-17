title: lua连接mysql
date: 2015-01-17 14:43:04
tags: [lua, mysql]
---

### my summary of using luasql

#### basic method

```
local luasql = require 'luasql.mysql'
local db_env = luasql.mysql()
local db_conn = db_env:connect(db_name, db_user, db_password, db_ip, db_port)
local cur = db_conn:execute('this is the sql syntax')

-- case insert: cur will be the number of the record which was been affected or nil
-- case query: cur wiil be userdata and row be table

local row = cur:fetch({}, flag)
-- the flag can be "a"  or "n"
-- case a: the index wiil be string or nil
-- case n: the index will be number or nil

cur:close()
-- if the cur is number, should not close this cur

db_conn:close()
db_env:close()
```

##### luasql also support the transation

```
db_conn:setautocommit(false)
cur == db_conn:execute("this is the sql syntax")
if cur == nil then db_conn:rollback() end
cur == db_conn:execute("this is the sql syntax")
if cur == nil then db_conn:rollback() end
db_conn:commit()
```

