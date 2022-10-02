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

> Display name with exactly 4 alphabets
```sql
select ename from emp
where enmae like '____';
```

> Display name with second letter as 'L'

```sql
select ename from emp
where ename like '_L%';
```

> Display name with fourth letter as 'M'

```sql
select ename from emp
where ename like '___M%';
```

> Display name with exactly 2 'L'
```sql
select enmae from emp
where ename like '%LL%';
```

> Name start with 'J' and ends with 'S'
```sql
select ename from emp 
where ename like 'J%S';
```

- **Display nth row**
```sql
-- assume nth row as 4th row
select * from emp
where rownum <= 4 -- rownum doesn't work with greater than
minus -- eliminates common records
select * from emp 
where rownum <= 3;
```

```sql
select * from (
    select rownum r, emp.* from emp
) where r = 4;
```

- **Union vs Union all**
<br>
can be used for single or multiple columns of same data type

```sql
select ename from emp1
union   -- eliminates all duplicate values and displays only unique ename
select ename from emp2;

select ename from emp1
union all   -- does not eliminates duplicate values.
select ename from emp2;

```
