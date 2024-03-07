# MySQL学习

## 1 基础知识

### 1.1 常用命令

注意，MySQL不见分号 ; 不执行

可以输入`\c`终止命令的输入



#### 本地登录

在终端中登录（隐式）：

`mysql -uroot -p`

然后再输入密码

#### 退出MySQL

`exit`

#### 查看MySQL中有哪些数据库

`show databases;`

注意，以分号结尾

#### 选择使用数据库

`use name;`

name是要使用的数据库名称

#### 创建数据库

`create database name;`

name是要创建的数据库名称

#### 查看某个数据库下的表

`show tables;`

#### 查看表中的数据

`select * from tablename;`  -  查看名为tablename的表的所有数据

`desc tablename;` - 查看名为tablename的表的结构

#### 查看当前使用的数据库

`select database();`


### 1.2 数据库中最基本的单元：表

数据库当中以表的形式表示数据，因为表比较直观

任何一张表都有**行**和**列**

行(row):称为**记录**/数据

列(column):称为**字段**

每一个字段都有：字段名、数据类型和约束等属性

### 1.3 SQL语句分类

DQL:数据查询语言，带有`select`关键字的都是查询语句

DML:数据操作语言，对**表中**的数据进行增删改。例如`insert` `delete` `update`

DDL:数据定义语言，主要是对表的**结构**进行操作，`create` `drop` `alter`

TCL:事务控制语言

DCL:数据控制语言

### 1.3 查询

#### 1.3.1 简单查询

##### (1) 查询一个字段

命令: `select 字段名 from 表名;`

##### (2) 查询多个字段

用逗号 "," 隔开

命令: `select 字段名1,字段名2 from 表名;`

##### (3) 查询所有字段

可以把所有字段名都打上

或者使用命令`select * from tablename;` 但这种方式效率低、可读性差，不建议在开发中使用

##### (4) 给查询的列起别名

可以使用 `as` 关键字

命令: `select 字段名 as 别名 from 表名;`

注意，只是将查询的结果显示为修改的别名，并没有实际修改表中的字段名

**select语句不会进行修改操作**

![图1-3-1 其他情况](images/2024-03-07-16-15-24.png)

##### (5) 列参与计算

字段可以使用数学表达式

![图1-3-2 字段使用数学表达式](images/2024-03-07-16-19-47.png)

#### 1.3.2 条件查询

查询符合条件的数据

```MySQL
select
    字段名1,字段名2,...,字段名n
from
    表名
where
    条件;
```

![图1-3-3 查询条件](images/2024-03-07-16-24-52.png)

注意，在数据库当中，查询是否为空时不能使用 `=` 而要使用 `is null` 或者 `is not null`

查询工资为3000的员工编号和员工名：

![图1-3-4 查询示例1](images/2024-03-07-16-26-27.png)

#### 1.3.3 模糊查询

![图1-3-4 模糊查询](images/2024-03-07-17-28-45.png)

% 匹配任意多个字符

_ 匹配任意一个字符

### 1.4 排序

#### 1.4.1 默认是升序

例子如下，order by 后面跟的是根据什么排序

命令: 

```MySQL
select
    字段名1,字段名2,...,字段名n
from
    表名
order by
    sal;
```

#### 1.4.2 指定降序、指定升序

指定降序：

```MySQL
select
    字段名1,字段名2,...,字段名n
from
    表名
order by
    sal desc;
```

指定升序：

```MySQL
select
    字段名1,字段名2,...,字段名n
from
    表名
order by
    sal asc;
```

#### 1.4.3 按照多个字段排序

```MySQL
select
    字段名1,字段名2,...,字段名n
from
    表名
order by
    sal asc, ename asc;
```

意思是如果sal一样，再根据ename进行排序（在前面的起主导，只有前面的都相等了再根据后面的来排序）

#### 1.4.4 综合案例1

![图1-4-1 多个关键字的顺序](images/2024-03-07-17-09-01.png)

### 1.5 单行处理函数

![图1-5-1 单行处理函数](images/2024-03-07-17-14-12.png)

单行处理函数：一个输入对应一个输出

多行处理函数：多个输入对应多个输出

### 1.6 分组函数/多行处理函数

分组函数在使用时必须先进行分组才能使用，若没有对数据进行分组，则整张表默认为一组

![图1-6-1 几个多行处理函数](images/2024-03-07-17-56-05.png)

注意：

1. 分组函数自动忽略NULL

### 1.6 连接查询

在一张表中查询数据，称为**单表查询**

多张表联合起来的**跨表查询数据**，称为**连接查询**

连接查询时需要加条件，只有满足条件的才会筛选出来，否则就会产生笛卡尔积现象

![图1-6-1 连接查询示例1](images/2024-03-07-18-16-38.png)

![图1-6-2 表起别名](images/2024-03-07-18-18-47.png)

#### 1.6.1 内连接

##### (1) 等值连接

案例：查询每个员工的部门，要求显示员工名和对应的部门名

-> 将emp e 和 dept d 两张表进行连接，条件是 e.deptno = d.deptno

SQL92语法：

```mysql
select
    e.ename,d.dname
from
    emp e,dept d
 where e.deptno = d.deptno;
```

SQL99语法：

```MySQL
select
    e.ename,d.dname
from
    emp e
join
    dept d
 on 
    e.deptno = d.deptno;
```

##### (2) 非等值连接

```mysql
select
    e.ename,e.sal,s.grade
from
    emp e join salgrade s
on
    e.sal between s.losal and s.hisal;
```

条件不是一个等值关系，称为非等值连接

##### (3) 自连接

把一张表看作两张表

```MySQL
select a.ename as '员工名',b.ename as '领导名'
from emp a join emp b
on a.mgr = b.empno;
```

#### 1.6.2 外连接

内连接是将和条件完全匹配的数据显示出来

```MySQL
select
    e.ename,d.dname
from
    emp e
right join
    dept d
 on 
    e.deptno = d.deptno;
```

![图1-6-1 外连接示例1](images/2024-03-07-18-52-49.png)

![图1-6-2 左外连接和右外连接](images/2024-03-07-18-55-46.png)

