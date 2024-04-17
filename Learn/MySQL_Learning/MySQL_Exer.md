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

### 1.7 设置小数位数

```sql
round(x, d)
```

其中，`x` 为要四舍五入的数字，`d` 为小数位数

### 1.8 having

在 SQL 中增加 `HAVING` 子句原因是，WHERE 关键字无法与聚合函数一起使用

`HAVING` 子句可以让我们筛选分组后的各组数据

```sql
select
    university,
    round(avg(question_cnt), 3) as avg_question_cnt,
    round(avg(answer_cnt), 3) as avg_answer_cnt
from
    user_profile
group by
    university
having
    avg_question_cnt < 5 or avg_answer_cnt < 20;
```

上述执行的结果为：按照学校进行分组，取出user_profile表中平均发贴数低于5的学校或平均回帖数小于20的学校。

不能用 `where` 的原因是如果使用 `where avg_question_cnt < 5 or avg_answer_cnt < 20` 进行过滤，这时候 
```sql
round(avg(question_cnt), 3) as avg_question_cnt
round(avg(answer_cnt), 3) as avg_answer_cnt
```
这两条语句还没有执行，自然也就没有 `avg_question_cnt` 和`avg_answer_cnt` 这时候执行`where`语句就会报错

### 1.9 语句执行顺序

MySQL语法顺序如下：

```sql
(7) SELECT
(8) DISTINCT <select_list>
(1) FROM  <main_table>
(3) <join_type> JOIN <join_table>
(2) ON <join_condition>
(4) WHERE <where_condition>
(5) GROUP BY <group_by_list>
(6) HAVING <having_condition>
(9) ORDER BY <order_by_condition>
(10) LIMIT <limit_number>
```

MySQL执行顺序则为左边的编号即：

FROM → ON → JOIN → WHERE → GROUP BY → HAVING → SELECT →DISTINCT → ORDER BY→ LIMIT

```sql
FROM  <main_table>
ON <join_condition>
<join_type> JOIN <join_table>
WHERE <where_condition>
GROUP BY <group_by_list>
HAVING <having_condition>
SELECT
DISTINCT <select_list>
ORDER BY <order_by_condition>
LIMIT <limit_number>
```