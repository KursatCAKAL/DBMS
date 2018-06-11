# DBMS
<h2>SQL Query Exercises </h2>

1. Select fname, mnt,
lname and dname of employees and the department each works n.
2. Produce a List
of employees, fname, lname, salary, n
order of ncreasng
salary.
3. Produce a List
of employees, fname, lname, salary, n
order of decreasng
salary.
4. Retreve
the names of all employees n
department 5 who work more than 10 hours on the "ProductX"
project.
5. Retreve
the names of all employees who work on the "ProductX" project less than 20 hours.
6. List
the names of all employees who have a dependent wth
the same frst
name as themselves.
7. Fnd
the names of all employees who are drectly
supervsed
by Frankln
Wong (You are NOT to use
Frankln's
SSN n
ths
query).
8. For each project, List
the project name and the total hours per week (by all employees) spent on that
project.
9. List
the names of employees who work on every project.
10. List
the names of all employees who do not work on any project.
11. For each department, retreve
the department name and the average salary of all employees workng
n
the department.
12. Fnd
the names and addresses of all employees who work on at least one project located n
Houston
but whose department has no locaton
n
Houston (Ths
s
a trcky
one).
13. List
the names of all department managers who have no dependents.

/*Answer 1*/
Select *
From employee as e,department as d
Where e.dno=d.dnumber
/*Answer 2*/
select *
from employee
order by Salary asc
/*Answer 3*/
select *
from employee
order by Salary dec
/*Answer 4*/
select *
from employee as e,project as p,works_on as w
where e.Dno=5 and p.pnumber=w.pno and w.essn=e.ssn and p.pname='ProductX'
having w.hours>10
/*Answer 4_Powered By Dname*/
select *
from employee as e,project as p,works_on as w
where e.Dno=(select Dnumber from department where Dname='Research') and
p.pnumber=w.pno and w.essn=e.ssn and p.pname='ProductX'
having w.hours>10
/*Answer 5*/
select *
from employee as e,project as p,works_on as w
where e.Ssn=w.Essn and w.pno=p.pnumber and p.pname='ProductY'
having w.Hours<20
/*Answer 6*/
select *
from employee as e,dependent as d
where e.ssn=d.essn and e.fname=d.dependent_name
/*Answer 7*/
SELECT *
FROM Employee as E
Where E.Superssn=(select Ssn from employee as S where S.Fname='Franklin'
and S.Lname='Wong')
/*Answer 8*/
select *,SUM(w.hours)
FROM Project as p,Works_on as w,Employee as e
Where p.pnumber=w.pno and e.ssn=w.essn
group by Pname
/*Answer 9*/
select *,Count(*)
from employee as e,works_on as w,project as p
where e.ssn=w.essn and p.pnumber=w.pno
group by e.Fname
having Count(*)>=(select Count(*) from project)/*Answer 10*/
select *,Count(*)
from employee as e,works_on as w,project as p
where e.ssn=w.essn and p.pnumber=w.pno
group by e.Fname
having Count(*)=0
/*Answer 11*/
select *,count(*),AVG(e.Salary)
from department as d,employee as e
where d.dnumber=e.dno
group by d.dname
/*Answer 12*/
select *,Count(*)
from employee as e,project as p,works_on as w
where e.ssn=w.essn and p.Pnumber=w.Pno and P.Plocation='Houston'
AND e.dno not in
(select Dnumber from Dept_Locations where Dlocation='Houston')
group by e.Fname
/*Answer 13*/
select *,Count(*)
from (employee as e join department as d) left outer join dependent as de
on e.ssn=de.Essn
where e.ssn=d.mgrssn and (de.essn IS NULL and de.dependent_name IS NULL)
group by Fname
/*Bot is no deparment manager and has not a dependent*/
select *,Count(*)
from (employee as e left outer join department as d on e.ssn=d.mgrssn) left
outer join dependent as de on e.ssn=de.Essn
group by Fname
select *,Count(*)
from (employee as e left outer join department as d on e.ssn=d.mgrssn)
left outer join dependent as de on e.ssn=de.Essn
where de.essn IS NULL and d.dnumber IS NULL
group by Fname
