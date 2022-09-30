## Sql Practice Problems
<br>

- **Second highest salary of an employee**
```sql
select max(sal) from emp
where sal not in (select max(sal) from emp);
```

```sql
select max(sal) from emp
where sal < (select max(sal) from emp);
```
- **Department wise highest Salary**
```sql
select max(sal), deptno 
from emp
group by deptno;
```

- **Department wise count of employees**
```sql
select count(*), deptno
from emp 
group by deptno;
```

- **Display alternate records**
```sql
select * from (
    select empno, ename, sal, rownum rn 
    from emp
    order by rn -- so that records are not random. This is not necessary
)
where mod(rn, 2) <> 0;
```

- **Display frequeny of elements in a column**
```sql
select ename, count(*) 
from emp
group by ename;
```

- **Display duplicate elements in a column**
```sql
select ename, count(*)
from emp
group by ename
having count(*) > 1; -- can't use where with group by
```

- **Pattern matching**
> Display names starting with 'M'

```sql
select ename from emp
where ename like 'M%';
```

> Display name ending with 'M'

```sql
select ename from emp
where ename like '%M';
```

> Display names having letter 'M'.

```sql
select ename from emp
where ename like '%M%';
```

> Display name that don't contain any 'M'

```sql
select ename from emp
where ename NOT like '%M%';
```
