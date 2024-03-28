# MySQL 34道题

## 1 取得每个部门最高薪水的人员名称

第1步：找到每个部门的最高薪水

```MySQL
select
    max(sal) as max_sal, deptno
from
    emp
group by deptno;
```

select max(sal) as max_sal, deptno from emp group by deptno;

```MySQL
select
    e.ename, t.*
from
    emp e
join
    (select max(sal) as max_sal, deptno from emp group by deptno) t
on
    e.deptno = t.deptno and e.sal = t.max_sal;
```

## 2 哪些人的薪水在部门的平均薪水之上

```MySQL
select
    deptno, avg(sal)
from
    emp
group by deptno;
```
select deptno, avg(sal) from emp group by deptno;

```MySQL
select
    e.ename, e.sal
from
    emp e
join
    (select deptno, avg(sal) as avg_sal from emp group by deptno) t
on
    e.deptno = t.deptno and e.sal > t.avg_sal;
```