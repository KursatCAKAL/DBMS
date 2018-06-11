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
<!-- HTML generated using hilite.me --><div style="background: #ffffff; overflow:auto;width:auto;border:solid gray;border-width:.1em .1em .1em .8em;padding:.2em .6em;"><pre style="margin: 0; line-height: 125%"><span style="color: #333333">/*</span>Answer <span style="color: #0000DD; font-weight: bold">1</span><span style="color: #333333">*/</span>
Select <span style="color: #333333">*</span>
From employee <span style="color: #008800; font-weight: bold">as</span> e,department <span style="color: #008800; font-weight: bold">as</span> d
Where e<span style="color: #333333">.</span>dno<span style="color: #333333">=</span>d<span style="color: #333333">.</span>dnumber
<span style="color: #333333">/*</span>Answer <span style="color: #0000DD; font-weight: bold">2</span><span style="color: #333333">*/</span>
select <span style="color: #333333">*</span>
<span style="color: #008800; font-weight: bold">from</span> <span style="color: #0e84b5; font-weight: bold">employee</span>
order by Salary asc
<span style="color: #333333">/*</span>Answer <span style="color: #0000DD; font-weight: bold">3</span><span style="color: #333333">*/</span>
select <span style="color: #333333">*</span>
<span style="color: #008800; font-weight: bold">from</span> <span style="color: #0e84b5; font-weight: bold">employee</span>
order by Salary dec
<span style="color: #333333">/*</span>Answer <span style="color: #0000DD; font-weight: bold">4</span><span style="color: #333333">*/</span>
select <span style="color: #333333">*</span>
<span style="color: #008800; font-weight: bold">from</span> <span style="color: #0e84b5; font-weight: bold">employee</span> <span style="color: #0e84b5; font-weight: bold">as</span> <span style="color: #0e84b5; font-weight: bold">e</span>,project <span style="color: #008800; font-weight: bold">as</span> p,works_on <span style="color: #008800; font-weight: bold">as</span> w
where e<span style="color: #333333">.</span>Dno<span style="color: #333333">=</span><span style="color: #0000DD; font-weight: bold">5</span> <span style="color: #000000; font-weight: bold">and</span> p<span style="color: #333333">.</span>pnumber<span style="color: #333333">=</span>w<span style="color: #333333">.</span>pno <span style="color: #000000; font-weight: bold">and</span> w<span style="color: #333333">.</span>essn<span style="color: #333333">=</span>e<span style="color: #333333">.</span>ssn <span style="color: #000000; font-weight: bold">and</span> p<span style="color: #333333">.</span>pname<span style="color: #333333">=</span><span style="background-color: #fff0f0">&#39;ProductX&#39;</span>
having w<span style="color: #333333">.</span>hours<span style="color: #333333">&gt;</span><span style="color: #0000DD; font-weight: bold">10</span>
<span style="color: #333333">/*</span>Answer <span style="color: #0000DD; font-weight: bold">4</span>_Powered By Dname<span style="color: #333333">*/</span>
select <span style="color: #333333">*</span>
<span style="color: #008800; font-weight: bold">from</span> <span style="color: #0e84b5; font-weight: bold">employee</span> <span style="color: #0e84b5; font-weight: bold">as</span> <span style="color: #0e84b5; font-weight: bold">e</span>,project <span style="color: #008800; font-weight: bold">as</span> p,works_on <span style="color: #008800; font-weight: bold">as</span> w
where e<span style="color: #333333">.</span>Dno<span style="color: #333333">=</span>(select Dnumber <span style="color: #008800; font-weight: bold">from</span> <span style="color: #0e84b5; font-weight: bold">department</span> <span style="color: #0e84b5; font-weight: bold">where</span> <span style="color: #0e84b5; font-weight: bold">Dname</span><span style="color: #333333">=</span><span style="background-color: #fff0f0">&#39;Research&#39;</span>) <span style="color: #000000; font-weight: bold">and</span>
p<span style="color: #333333">.</span>pnumber<span style="color: #333333">=</span>w<span style="color: #333333">.</span>pno <span style="color: #000000; font-weight: bold">and</span> w<span style="color: #333333">.</span>essn<span style="color: #333333">=</span>e<span style="color: #333333">.</span>ssn <span style="color: #000000; font-weight: bold">and</span> p<span style="color: #333333">.</span>pname<span style="color: #333333">=</span><span style="background-color: #fff0f0">&#39;ProductX&#39;</span>
having w<span style="color: #333333">.</span>hours<span style="color: #333333">&gt;</span><span style="color: #0000DD; font-weight: bold">10</span>
<span style="color: #333333">/*</span>Answer <span style="color: #0000DD; font-weight: bold">5</span><span style="color: #333333">*/</span>
select <span style="color: #333333">*</span>
<span style="color: #008800; font-weight: bold">from</span> <span style="color: #0e84b5; font-weight: bold">employee</span> <span style="color: #0e84b5; font-weight: bold">as</span> <span style="color: #0e84b5; font-weight: bold">e</span>,project <span style="color: #008800; font-weight: bold">as</span> p,works_on <span style="color: #008800; font-weight: bold">as</span> w
where e<span style="color: #333333">.</span>Ssn<span style="color: #333333">=</span>w<span style="color: #333333">.</span>Essn <span style="color: #000000; font-weight: bold">and</span> w<span style="color: #333333">.</span>pno<span style="color: #333333">=</span>p<span style="color: #333333">.</span>pnumber <span style="color: #000000; font-weight: bold">and</span> p<span style="color: #333333">.</span>pname<span style="color: #333333">=</span><span style="background-color: #fff0f0">&#39;ProductY&#39;</span>
having w<span style="color: #333333">.</span>Hours<span style="color: #333333">&lt;</span><span style="color: #0000DD; font-weight: bold">20</span>
<span style="color: #333333">/*</span>Answer <span style="color: #0000DD; font-weight: bold">6</span><span style="color: #333333">*/</span>
select <span style="color: #333333">*</span>
<span style="color: #008800; font-weight: bold">from</span> <span style="color: #0e84b5; font-weight: bold">employee</span> <span style="color: #0e84b5; font-weight: bold">as</span> <span style="color: #0e84b5; font-weight: bold">e</span>,dependent <span style="color: #008800; font-weight: bold">as</span> d
where e<span style="color: #333333">.</span>ssn<span style="color: #333333">=</span>d<span style="color: #333333">.</span>essn <span style="color: #000000; font-weight: bold">and</span> e<span style="color: #333333">.</span>fname<span style="color: #333333">=</span>d<span style="color: #333333">.</span>dependent_name
<span style="color: #333333">/*</span>Answer <span style="color: #0000DD; font-weight: bold">7</span><span style="color: #333333">*/</span>
SELECT <span style="color: #333333">*</span>
FROM Employee <span style="color: #008800; font-weight: bold">as</span> E
Where E<span style="color: #333333">.</span>Superssn<span style="color: #333333">=</span>(select Ssn <span style="color: #008800; font-weight: bold">from</span> <span style="color: #0e84b5; font-weight: bold">employee</span> <span style="color: #0e84b5; font-weight: bold">as</span> <span style="color: #0e84b5; font-weight: bold">S</span> <span style="color: #0e84b5; font-weight: bold">where</span> <span style="color: #0e84b5; font-weight: bold">S.Fname</span><span style="color: #333333">=</span><span style="background-color: #fff0f0">&#39;Franklin&#39;</span>
<span style="color: #000000; font-weight: bold">and</span> S<span style="color: #333333">.</span>Lname<span style="color: #333333">=</span><span style="background-color: #fff0f0">&#39;Wong&#39;</span>)
<span style="color: #333333">/*</span>Answer <span style="color: #0000DD; font-weight: bold">8</span><span style="color: #333333">*/</span>
select <span style="color: #333333">*</span>,SUM(w<span style="color: #333333">.</span>hours)
FROM Project <span style="color: #008800; font-weight: bold">as</span> p,Works_on <span style="color: #008800; font-weight: bold">as</span> w,Employee <span style="color: #008800; font-weight: bold">as</span> e
Where p<span style="color: #333333">.</span>pnumber<span style="color: #333333">=</span>w<span style="color: #333333">.</span>pno <span style="color: #000000; font-weight: bold">and</span> e<span style="color: #333333">.</span>ssn<span style="color: #333333">=</span>w<span style="color: #333333">.</span>essn
group by Pname
<span style="color: #333333">/*</span>Answer <span style="color: #0000DD; font-weight: bold">9</span><span style="color: #333333">*/</span>
select <span style="color: #333333">*</span>,Count(<span style="color: #333333">*</span>)
<span style="color: #008800; font-weight: bold">from</span> <span style="color: #0e84b5; font-weight: bold">employee</span> <span style="color: #0e84b5; font-weight: bold">as</span> <span style="color: #0e84b5; font-weight: bold">e</span>,works_on <span style="color: #008800; font-weight: bold">as</span> w,project <span style="color: #008800; font-weight: bold">as</span> p
where e<span style="color: #333333">.</span>ssn<span style="color: #333333">=</span>w<span style="color: #333333">.</span>essn <span style="color: #000000; font-weight: bold">and</span> p<span style="color: #333333">.</span>pnumber<span style="color: #333333">=</span>w<span style="color: #333333">.</span>pno
group by e<span style="color: #333333">.</span>Fname
having Count(<span style="color: #333333">*</span>)<span style="color: #333333">&gt;=</span>(select Count(<span style="color: #333333">*</span>) <span style="color: #008800; font-weight: bold">from</span> <span style="color: #0e84b5; font-weight: bold">project</span>)<span style="color: #333333">/*</span>Answer <span style="color: #0000DD; font-weight: bold">10</span><span style="color: #333333">*/</span>
select <span style="color: #333333">*</span>,Count(<span style="color: #333333">*</span>)
<span style="color: #008800; font-weight: bold">from</span> <span style="color: #0e84b5; font-weight: bold">employee</span> <span style="color: #0e84b5; font-weight: bold">as</span> <span style="color: #0e84b5; font-weight: bold">e</span>,works_on <span style="color: #008800; font-weight: bold">as</span> w,project <span style="color: #008800; font-weight: bold">as</span> p
where e<span style="color: #333333">.</span>ssn<span style="color: #333333">=</span>w<span style="color: #333333">.</span>essn <span style="color: #000000; font-weight: bold">and</span> p<span style="color: #333333">.</span>pnumber<span style="color: #333333">=</span>w<span style="color: #333333">.</span>pno
group by e<span style="color: #333333">.</span>Fname
having Count(<span style="color: #333333">*</span>)<span style="color: #333333">=</span><span style="color: #0000DD; font-weight: bold">0</span>
<span style="color: #333333">/*</span>Answer <span style="color: #0000DD; font-weight: bold">11</span><span style="color: #333333">*/</span>
select <span style="color: #333333">*</span>,count(<span style="color: #333333">*</span>),AVG(e<span style="color: #333333">.</span>Salary)
<span style="color: #008800; font-weight: bold">from</span> <span style="color: #0e84b5; font-weight: bold">department</span> <span style="color: #0e84b5; font-weight: bold">as</span> <span style="color: #0e84b5; font-weight: bold">d</span>,employee <span style="color: #008800; font-weight: bold">as</span> e
where d<span style="color: #333333">.</span>dnumber<span style="color: #333333">=</span>e<span style="color: #333333">.</span>dno
group by d<span style="color: #333333">.</span>dname
<span style="color: #333333">/*</span>Answer <span style="color: #0000DD; font-weight: bold">12</span><span style="color: #333333">*/</span>
select <span style="color: #333333">*</span>,Count(<span style="color: #333333">*</span>)
<span style="color: #008800; font-weight: bold">from</span> <span style="color: #0e84b5; font-weight: bold">employee</span> <span style="color: #0e84b5; font-weight: bold">as</span> <span style="color: #0e84b5; font-weight: bold">e</span>,project <span style="color: #008800; font-weight: bold">as</span> p,works_on <span style="color: #008800; font-weight: bold">as</span> w
where e<span style="color: #333333">.</span>ssn<span style="color: #333333">=</span>w<span style="color: #333333">.</span>essn <span style="color: #000000; font-weight: bold">and</span> p<span style="color: #333333">.</span>Pnumber<span style="color: #333333">=</span>w<span style="color: #333333">.</span>Pno <span style="color: #000000; font-weight: bold">and</span> P<span style="color: #333333">.</span>Plocation<span style="color: #333333">=</span><span style="background-color: #fff0f0">&#39;Houston&#39;</span>
AND e<span style="color: #333333">.</span>dno <span style="color: #000000; font-weight: bold">not</span> <span style="color: #000000; font-weight: bold">in</span>
(select Dnumber <span style="color: #008800; font-weight: bold">from</span> <span style="color: #0e84b5; font-weight: bold">Dept_Locations</span> <span style="color: #0e84b5; font-weight: bold">where</span> <span style="color: #0e84b5; font-weight: bold">Dlocation</span><span style="color: #333333">=</span><span style="background-color: #fff0f0">&#39;Houston&#39;</span>)
group by e<span style="color: #333333">.</span>Fname
<span style="color: #333333">/*</span>Answer <span style="color: #0000DD; font-weight: bold">13</span><span style="color: #333333">*/</span>
select <span style="color: #333333">*</span>,Count(<span style="color: #333333">*</span>)
<span style="color: #008800; font-weight: bold">from</span> (employee <span style="color: #008800; font-weight: bold">as</span> e join department <span style="color: #008800; font-weight: bold">as</span> d) left outer join dependent <span style="color: #008800; font-weight: bold">as</span> de
on e<span style="color: #333333">.</span>ssn<span style="color: #333333">=</span>de<span style="color: #333333">.</span>Essn
where e<span style="color: #333333">.</span>ssn<span style="color: #333333">=</span>d<span style="color: #333333">.</span>mgrssn <span style="color: #000000; font-weight: bold">and</span> (de<span style="color: #333333">.</span>essn IS NULL <span style="color: #000000; font-weight: bold">and</span> de<span style="color: #333333">.</span>dependent_name IS NULL)
group by Fname
<span style="color: #333333">/*</span>Bot <span style="color: #000000; font-weight: bold">is</span> no deparment manager <span style="color: #000000; font-weight: bold">and</span> has <span style="color: #000000; font-weight: bold">not</span> a dependent<span style="color: #333333">*/</span>
select <span style="color: #333333">*</span>,Count(<span style="color: #333333">*</span>)
<span style="color: #008800; font-weight: bold">from</span> (employee <span style="color: #008800; font-weight: bold">as</span> e left outer join department <span style="color: #008800; font-weight: bold">as</span> d on e<span style="color: #333333">.</span>ssn<span style="color: #333333">=</span>d<span style="color: #333333">.</span>mgrssn) left
outer join dependent <span style="color: #008800; font-weight: bold">as</span> de on e<span style="color: #333333">.</span>ssn<span style="color: #333333">=</span>de<span style="color: #333333">.</span>Essn
group by Fname
select <span style="color: #333333">*</span>,Count(<span style="color: #333333">*</span>)
<span style="color: #008800; font-weight: bold">from</span> (employee <span style="color: #008800; font-weight: bold">as</span> e left outer join department <span style="color: #008800; font-weight: bold">as</span> d on e<span style="color: #333333">.</span>ssn<span style="color: #333333">=</span>d<span style="color: #333333">.</span>mgrssn)
left outer join dependent <span style="color: #008800; font-weight: bold">as</span> de on e<span style="color: #333333">.</span>ssn<span style="color: #333333">=</span>de<span style="color: #333333">.</span>Essn
where de<span style="color: #333333">.</span>essn IS NULL <span style="color: #000000; font-weight: bold">and</span> d<span style="color: #333333">.</span>dnumber IS NULL
group by Fname
</pre></div>

