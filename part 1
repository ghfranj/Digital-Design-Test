
/*First q:*/
select * from [DigitalDesign].[dbo].EMPLOYEE
where SALARY = (select max(SALARY) from [DigitalDesign].[dbo].EMPLOYEE);
/*--------------*/
/*Second q:*/
Go
with 
em_ch(ID, CHIEF_ID,depth) as (
select ID, CHIEF_ID, 0 INT from [DigitalDesign].[dbo].EMPLOYEE
),
emp(ID, CHIEF_ID, depth) as (
select ID, CHIEF_ID, 0 INT from [DigitalDesign].[dbo].[EMPLOYEE] as e 
where e.ID not in (select e2.CHIEF_ID from [DigitalDesign].[dbo].EMPLOYEE as e2 where e2.CHIEF_ID IS NOT NULL)
),
em_ch_dep(ID, CHIEF_ID, depth) as (
select * from emp
union all
select a.ID, b.CHIEF_ID, a.depth + 1 from em_ch_dep as a join
[DigitalDesign].[dbo].EMPLOYEE as b on b.ID = a.CHIEF_ID 
)

select max(depth) as max_depth from em_ch_dep


/*---------------*/
/*Third q:*/
Go
WITH dep_sal_sum
AS (select DEPARTMENT_ID, sum(SALARY) as SALARY_SUM
	from [DigitalDesign].[dbo].[EMPLOYEE] 
	group by DEPARTMENT_ID
)
select * from [DigitalDesign].[dbo].DEPARTMENT
where ID = (select DEPARTMENT_ID from dep_sal_sum 
			where SALARY_SUM = (select max(SALARY_SUM) from dep_sal_sum ) );
/*----------------*/
/*Fourth q:*/
Go
select TOP 1 * from [DigitalDesign].[dbo].EMPLOYEE
where NAME like 'R%n';


