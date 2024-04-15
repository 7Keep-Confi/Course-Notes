# MySQL刷题

## 1 基础

### 1.1 查询结果去重

查询结果去重可以使用 `distinct` 

`SELECT DISTINCT` 语句用于返回唯一不同的值

```sql
select distinct 
    university
from
    user_profile;
```

对user_profile表中university字段中的值进行去重，并返回查询结果

### 1.2 对查询列重命名

对查询后的列重命名可以使用 `as`

```sql
select 
    device_id as user_infos_example
from
    user_profile
limit 0,2;
```

该语句的结果为，返回user_profile表中字段为device_id的前两个值，并将查询列重命名为user_infos_example

### 1.3 过滤空值

过滤空值可以使用 `is not NULL`

### 1.4 基础排序:order by

order by 字段名 asc;  表示按照字段名进行升序排列，asc可以省略不写，因为默认是按照升序排序

order by 字段名 desc;  表示按照字段名进行降序排列

### 1.5 where in 和 not in

WHERE column IN (value1,value2,...)

表示满足列表项(value1, value2, ...)之一的结果

WHERE column NOT IN (value1,value2,...)

表示不满足列表项(value1, value2, ...)的结果

### 1.6 模糊查询：like

```sql
select
    device_id, age, university
from
    user_profile
where
    university like '北京%';
```

注意：

* %表示匹配任意多个（0个或多个）字符
* _表示匹配任意一个字符
* [ ]代表匹配其中的任意一个字符
* [^]代表取反的意思，不匹配中的任意一个字符

例如：

```sql
SELECT * FROM t_user WHERE u_name LIKE '[张李王]三';
```

表示匹配括号内所列字符中的一个

表示匹配张三、李三和王三

```sql
SELECT * FROM t_user WHERE u_name LIKE '[^张李王]三';
```

表示不在括号所列之内的单个字符