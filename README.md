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

