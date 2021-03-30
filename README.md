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

<h2>Answers</h2>




<!-- HTML generated using hilite.me --><div style="background: #ffffff; overflow:auto;width:auto;border:solid gray;border-width:.1em .1em .1em .8em;padding:.2em .6em;"><pre style="margin: 0; line-height: 125%"><span style="color: #888888">/*Answer 1*/</span>
<span style="color: #008800; font-weight: bold">Select</span> <span style="color: #333333">*</span>
<span style="color: #008800; font-weight: bold">From</span> employee <span style="color: #008800; font-weight: bold">as</span> e,department <span style="color: #008800; font-weight: bold">as</span> d
<span style="color: #008800; font-weight: bold">Where</span> e.dno<span style="color: #333333">=</span>d.dnumber

<span style="color: #888888">/*Answer 2*/</span>
<span style="color: #008800; font-weight: bold">select</span> <span style="color: #333333">*</span>
<span style="color: #008800; font-weight: bold">from</span> employee 
<span style="color: #008800; font-weight: bold">order</span> <span style="color: #008800; font-weight: bold">by</span> Salary <span style="color: #008800; font-weight: bold">asc</span>

<span style="color: #888888">/*Answer 3*/</span>
<span style="color: #008800; font-weight: bold">select</span> <span style="color: #333333">*</span>
<span style="color: #008800; font-weight: bold">from</span> employee 
<span style="color: #008800; font-weight: bold">order</span> <span style="color: #008800; font-weight: bold">by</span> Salary <span style="color: #007020">dec</span>

<span style="color: #888888">/*Answer 4*/</span>
<span style="color: #008800; font-weight: bold">select</span> <span style="color: #333333">*</span>
<span style="color: #008800; font-weight: bold">from</span> employee <span style="color: #008800; font-weight: bold">as</span> e,project <span style="color: #008800; font-weight: bold">as</span> p,works_on <span style="color: #008800; font-weight: bold">as</span> w
<span style="color: #008800; font-weight: bold">where</span> e.Dno<span style="color: #333333">=</span><span style="color: #0000DD; font-weight: bold">5</span> <span style="color: #008800; font-weight: bold">and</span> p.pnumber<span style="color: #333333">=</span>w.pno <span style="color: #008800; font-weight: bold">and</span> w.essn<span style="color: #333333">=</span>e.ssn <span style="color: #008800; font-weight: bold">and</span> p.pname<span style="color: #333333">=</span><span style="background-color: #fff0f0">&#39;ProductX&#39;</span>
<span style="color: #008800; font-weight: bold">having</span> w.hours<span style="color: #333333">&gt;</span><span style="color: #0000DD; font-weight: bold">10</span>

<span style="color: #888888">/*Answer 4_Powered By Dname*/</span>
<span style="color: #008800; font-weight: bold">select</span> <span style="color: #333333">*</span>
<span style="color: #008800; font-weight: bold">from</span> employee <span style="color: #008800; font-weight: bold">as</span> e,project <span style="color: #008800; font-weight: bold">as</span> p,works_on <span style="color: #008800; font-weight: bold">as</span> w
<span style="color: #008800; font-weight: bold">where</span> e.Dno<span style="color: #333333">=</span>(<span style="color: #008800; font-weight: bold">select</span> Dnumber <span style="color: #008800; font-weight: bold">from</span> department <span style="color: #008800; font-weight: bold">where</span> Dname<span style="color: #333333">=</span><span style="background-color: #fff0f0">&#39;Research&#39;</span>) <span style="color: #008800; font-weight: bold">and</span> p.pnumber<span style="color: #333333">=</span>w.pno <span style="color: #008800; font-weight: bold">and</span> w.essn<span style="color: #333333">=</span>e.ssn <span style="color: #008800; font-weight: bold">and</span> p.pname<span style="color: #333333">=</span><span style="background-color: #fff0f0">&#39;ProductX&#39;</span>
<span style="color: #008800; font-weight: bold">having</span> w.hours<span style="color: #333333">&gt;</span><span style="color: #0000DD; font-weight: bold">10</span>

<span style="color: #888888">/*Answer 5*/</span>
<span style="color: #008800; font-weight: bold">select</span> <span style="color: #333333">*</span>
<span style="color: #008800; font-weight: bold">from</span> employee <span style="color: #008800; font-weight: bold">as</span> e,project <span style="color: #008800; font-weight: bold">as</span> p,works_on <span style="color: #008800; font-weight: bold">as</span> w
<span style="color: #008800; font-weight: bold">where</span> e.Ssn<span style="color: #333333">=</span>w.Essn <span style="color: #008800; font-weight: bold">and</span> w.pno<span style="color: #333333">=</span>p.pnumber <span style="color: #008800; font-weight: bold">and</span> p.pname<span style="color: #333333">=</span><span style="background-color: #fff0f0">&#39;ProductY&#39;</span>
<span style="color: #008800; font-weight: bold">having</span> w.Hours<span style="color: #333333">&lt;</span><span style="color: #0000DD; font-weight: bold">20</span>

<span style="color: #888888">/*Answer 6*/</span>
<span style="color: #008800; font-weight: bold">select</span> <span style="color: #333333">*</span>
<span style="color: #008800; font-weight: bold">from</span> employee <span style="color: #008800; font-weight: bold">as</span> e,dependent <span style="color: #008800; font-weight: bold">as</span> d
<span style="color: #008800; font-weight: bold">where</span> e.ssn<span style="color: #333333">=</span>d.essn <span style="color: #008800; font-weight: bold">and</span> e.fname<span style="color: #333333">=</span>d.dependent_name

<span style="color: #888888">/*Answer 7*/</span>
<span style="color: #008800; font-weight: bold">SELECT</span> <span style="color: #333333">*</span>
<span style="color: #008800; font-weight: bold">FROM</span> Employee <span style="color: #008800; font-weight: bold">as</span> E
<span style="color: #008800; font-weight: bold">Where</span> E.Superssn<span style="color: #333333">=</span>(<span style="color: #008800; font-weight: bold">select</span> Ssn <span style="color: #008800; font-weight: bold">from</span> employee <span style="color: #008800; font-weight: bold">as</span> S <span style="color: #008800; font-weight: bold">where</span> S.Fname<span style="color: #333333">=</span><span style="background-color: #fff0f0">&#39;Franklin&#39;</span> <span style="color: #008800; font-weight: bold">and</span> S.Lname<span style="color: #333333">=</span><span style="background-color: #fff0f0">&#39;Wong&#39;</span>)

<span style="color: #888888">/*Answer 8*/</span>
<span style="color: #008800; font-weight: bold">select</span> <span style="color: #333333">*</span>,<span style="color: #008800; font-weight: bold">SUM</span>(w.hours)
<span style="color: #008800; font-weight: bold">FROM</span> Project <span style="color: #008800; font-weight: bold">as</span> p,Works_on <span style="color: #008800; font-weight: bold">as</span> w,Employee <span style="color: #008800; font-weight: bold">as</span> e
<span style="color: #008800; font-weight: bold">Where</span> p.pnumber<span style="color: #333333">=</span>w.pno <span style="color: #008800; font-weight: bold">and</span> e.ssn<span style="color: #333333">=</span>w.essn
<span style="color: #008800; font-weight: bold">group</span> <span style="color: #008800; font-weight: bold">by</span> Pname

<span style="color: #888888">/*Answer 9*/</span>
<span style="color: #008800; font-weight: bold">select</span> <span style="color: #333333">*</span>,<span style="color: #008800; font-weight: bold">Count</span>(<span style="color: #333333">*</span>)
<span style="color: #008800; font-weight: bold">from</span> employee <span style="color: #008800; font-weight: bold">as</span> e,works_on <span style="color: #008800; font-weight: bold">as</span> w,project <span style="color: #008800; font-weight: bold">as</span> p
<span style="color: #008800; font-weight: bold">where</span> e.ssn<span style="color: #333333">=</span>w.essn <span style="color: #008800; font-weight: bold">and</span> p.pnumber<span style="color: #333333">=</span>w.pno
<span style="color: #008800; font-weight: bold">group</span> <span style="color: #008800; font-weight: bold">by</span> e.Fname
<span style="color: #008800; font-weight: bold">having</span> <span style="color: #008800; font-weight: bold">Count</span>(<span style="color: #333333">*</span>)<span style="color: #333333">&gt;=</span>(<span style="color: #008800; font-weight: bold">select</span> <span style="color: #008800; font-weight: bold">Count</span>(<span style="color: #333333">*</span>) <span style="color: #008800; font-weight: bold">from</span> project)

<span style="color: #888888">/*Answer 10*/</span>
<span style="color: #008800; font-weight: bold">select</span> <span style="color: #333333">*</span>,<span style="color: #008800; font-weight: bold">Count</span>(<span style="color: #333333">*</span>)
<span style="color: #008800; font-weight: bold">from</span> employee <span style="color: #008800; font-weight: bold">as</span> e,works_on <span style="color: #008800; font-weight: bold">as</span> w,project <span style="color: #008800; font-weight: bold">as</span> p
<span style="color: #008800; font-weight: bold">where</span> e.ssn<span style="color: #333333">=</span>w.essn <span style="color: #008800; font-weight: bold">and</span> p.pnumber<span style="color: #333333">=</span>w.pno
<span style="color: #008800; font-weight: bold">group</span> <span style="color: #008800; font-weight: bold">by</span> e.Fname
<span style="color: #008800; font-weight: bold">having</span> <span style="color: #008800; font-weight: bold">Count</span>(<span style="color: #333333">*</span>)<span style="color: #333333">=</span><span style="color: #0000DD; font-weight: bold">0</span>

<span style="color: #888888">/*Answer 11*/</span>
<span style="color: #008800; font-weight: bold">select</span> <span style="color: #333333">*</span>,<span style="color: #008800; font-weight: bold">count</span>(<span style="color: #333333">*</span>),<span style="color: #008800; font-weight: bold">AVG</span>(e.Salary)
<span style="color: #008800; font-weight: bold">from</span> department <span style="color: #008800; font-weight: bold">as</span> d,employee <span style="color: #008800; font-weight: bold">as</span> e
<span style="color: #008800; font-weight: bold">where</span> d.dnumber<span style="color: #333333">=</span>e.dno 
<span style="color: #008800; font-weight: bold">group</span> <span style="color: #008800; font-weight: bold">by</span> d.dname

<span style="color: #888888">/*Answer 12*/</span>
<span style="color: #008800; font-weight: bold">select</span> <span style="color: #333333">*</span>,<span style="color: #008800; font-weight: bold">Count</span>(<span style="color: #333333">*</span>)
<span style="color: #008800; font-weight: bold">from</span> employee <span style="color: #008800; font-weight: bold">as</span> e,project <span style="color: #008800; font-weight: bold">as</span> p,works_on <span style="color: #008800; font-weight: bold">as</span> w
<span style="color: #008800; font-weight: bold">where</span> e.ssn<span style="color: #333333">=</span>w.essn <span style="color: #008800; font-weight: bold">and</span> p.Pnumber<span style="color: #333333">=</span>w.Pno <span style="color: #008800; font-weight: bold">and</span> P.Plocation<span style="color: #333333">=</span><span style="background-color: #fff0f0">&#39;Houston&#39;</span> 
  <span style="color: #008800; font-weight: bold">AND</span> e.dno <span style="color: #008800; font-weight: bold">not</span> <span style="color: #008800; font-weight: bold">in</span>
  (<span style="color: #008800; font-weight: bold">select</span> Dnumber <span style="color: #008800; font-weight: bold">from</span> Dept_Locations <span style="color: #008800; font-weight: bold">where</span> Dlocation<span style="color: #333333">=</span><span style="background-color: #fff0f0">&#39;Houston&#39;</span>)
<span style="color: #008800; font-weight: bold">group</span> <span style="color: #008800; font-weight: bold">by</span> e.Fname


<span style="color: #888888">/*Answer 13*/</span>
<span style="color: #008800; font-weight: bold">select</span> <span style="color: #333333">*</span>,<span style="color: #008800; font-weight: bold">Count</span>(<span style="color: #333333">*</span>)
<span style="color: #008800; font-weight: bold">from</span> (employee <span style="color: #008800; font-weight: bold">as</span> e <span style="color: #008800; font-weight: bold">join</span> department <span style="color: #008800; font-weight: bold">as</span> d) <span style="color: #008800; font-weight: bold">left</span> <span style="color: #008800; font-weight: bold">outer</span> <span style="color: #008800; font-weight: bold">join</span> dependent <span style="color: #008800; font-weight: bold">as</span> de <span style="color: #008800; font-weight: bold">on</span> e.ssn<span style="color: #333333">=</span>de.Essn
<span style="color: #008800; font-weight: bold">where</span> e.ssn<span style="color: #333333">=</span>d.mgrssn <span style="color: #008800; font-weight: bold">and</span> (de.essn <span style="color: #008800; font-weight: bold">IS</span> <span style="color: #008800; font-weight: bold">NULL</span> <span style="color: #008800; font-weight: bold">and</span> de.dependent_name <span style="color: #008800; font-weight: bold">IS</span> <span style="color: #008800; font-weight: bold">NULL</span>)
<span style="color: #008800; font-weight: bold">group</span> <span style="color: #008800; font-weight: bold">by</span> Fname

<span style="color: #888888">/*Bot is no deparment manager and has not a dependent*/</span>
<span style="color: #008800; font-weight: bold">select</span> <span style="color: #333333">*</span>,<span style="color: #008800; font-weight: bold">Count</span>(<span style="color: #333333">*</span>)
<span style="color: #008800; font-weight: bold">from</span> (employee <span style="color: #008800; font-weight: bold">as</span> e <span style="color: #008800; font-weight: bold">left</span> <span style="color: #008800; font-weight: bold">outer</span> <span style="color: #008800; font-weight: bold">join</span> department <span style="color: #008800; font-weight: bold">as</span> d <span style="color: #008800; font-weight: bold">on</span> e.ssn<span style="color: #333333">=</span>d.mgrssn) <span style="color: #008800; font-weight: bold">left</span> <span style="color: #008800; font-weight: bold">outer</span> <span style="color: #008800; font-weight: bold">join</span> dependent <span style="color: #008800; font-weight: bold">as</span> de <span style="color: #008800; font-weight: bold">on</span> e.ssn<span style="color: #333333">=</span>de.Essn
<span style="color: #008800; font-weight: bold">group</span> <span style="color: #008800; font-weight: bold">by</span> Fname


<span style="color: #008800; font-weight: bold">select</span> <span style="color: #333333">*</span>,<span style="color: #008800; font-weight: bold">Count</span>(<span style="color: #333333">*</span>)
<span style="color: #008800; font-weight: bold">from</span> (employee <span style="color: #008800; font-weight: bold">as</span> e <span style="color: #008800; font-weight: bold">left</span> <span style="color: #008800; font-weight: bold">outer</span> <span style="color: #008800; font-weight: bold">join</span> department <span style="color: #008800; font-weight: bold">as</span> d <span style="color: #008800; font-weight: bold">on</span> e.ssn<span style="color: #333333">=</span>d.mgrssn) 
<span style="color: #008800; font-weight: bold">left</span> <span style="color: #008800; font-weight: bold">outer</span> <span style="color: #008800; font-weight: bold">join</span> dependent <span style="color: #008800; font-weight: bold">as</span> de <span style="color: #008800; font-weight: bold">on</span> e.ssn<span style="color: #333333">=</span>de.Essn
<span style="color: #008800; font-weight: bold">where</span> de.essn <span style="color: #008800; font-weight: bold">IS</span> <span style="color: #008800; font-weight: bold">NULL</span> <span style="color: #008800; font-weight: bold">and</span> d.dnumber <span style="color: #008800; font-weight: bold">IS</span> <span style="color: #008800; font-weight: bold">NULL</span>
<span style="color: #008800; font-weight: bold">group</span> <span style="color: #008800; font-weight: bold">by</span> Fname
</pre></div>

<a href="https://www.tutorialspoint.com/dbms/relational_algebra.htm" target="_blank">Relational Algebra</a>
