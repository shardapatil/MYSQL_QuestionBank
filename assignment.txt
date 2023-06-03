mysql> use cdac_nikhiassignment;
Database changed
mysql> 
mysql> CREATE TABLE DEPT
    -> (
    -> DEPTNO NUMERIC(2)  PRIMARY KEY,
    -> DNAME VARCHAR(14),
    -> LOC VARCHAR(13)
    -> );
Query OK, 0 rows affected (0.03 sec)

mysql> INSERT INTO DEPT VALUES(10,'ACCOUNTING','NEW YORK');
Query OK, 1 row affected (0.01 sec)

mysql> INSERT INTO DEPT VALUES(20,'RESEARCH','DALLAS');
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO DEPT VALUES(30,'SALES','CHICAGO');
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO DEPT VALUES(40,'OPERATIONS','BOSTON');
Query OK, 1 row affected (0.00 sec)

mysql> CREATE TABLE EMP
    -> (
    ->  EMPNO NUMERIC(4) PRIMARY KEY,
    ->  ENAME VARCHAR(10),
    ->  JOB   VARCHAR(9),
    ->  MGR   NUMERIC(4), 
    ->  HIREDATE DATE,
    ->  SAL NUMERIC(7,2),        
    ->  COMM NUMERIC(7,2),        
    ->  DEPTNO NUMERIC(2)  REFERENCES DEPT(DEPTNO)      
    -> );
Query OK, 0 rows affected (0.02 sec)

mysql> INSERT INTO EMP VALUES(7369,'SMITH','CLERK',7902,'2012-02-02',800,NULL,20);
Query OK, 1 row affected (0.02 sec)

mysql> INSERT INTO EMP VALUES(7499,'ALLEN','SALESMAN',7698,'2012-01-02',1600,300,30);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO EMP VALUES(7521,'WARD','SALESMAN',7698,'2013-01-02',1250,500,30);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO EMP VALUES(7566,'JONES','MANAGER',7839,'2013-01-02',2975,NULL,20);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO EMP VALUES(7654,'MARTIN','SALESMAN',7698,'2012-05-02',1250,1400,30);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO EMP VALUES(7698,'BLAKE','MANAGER',7839,'2012-01-06',2850,NULL,30);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO EMP VALUES(7782,'CLARK','MANAGER',7839,'2012-01-06',2450,NULL,10);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO EMP VALUES(7788,'SCOTT','ANALYST',7566,'2012-01-10',3000,NULL,20);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO EMP VALUES(7839,'KING','PRESIDENT',NULL,'2012-01-15',5000,NULL,10);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO EMP VALUES(7844,'TURNER','SALESMAN',7698,'2012-01-20',1500,0,30);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO EMP VALUES(7876,'ADAMS','CLERK',7788,'2013-01-02',1100,NULL,20);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO EMP VALUES(7900,'JAMES','CLERK',7698,'2012-03-02','950',NULL,30);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO EMP VALUES(7902,'FORD','ANALYST',7566,'2012-04-02',3000,NULL,20);
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO EMP VALUES(7934,'MILLER','CLERK',7782,'2012-05-02',1300,NULL,10); 
Query OK, 1 row affected (0.01 sec)

mysql> select * from emp where DEPTNO = 30;
+-------+--------+----------+------+------------+---------+---------+--------+
| EMPNO | ENAME  | JOB      | MGR  | HIREDATE   | SAL     | COMM    | DEPTNO |
+-------+--------+----------+------+------------+---------+---------+--------+
|  7499 | ALLEN  | SALESMAN | 7698 | 2012-01-02 | 1600.00 |  300.00 |     30 |
|  7521 | WARD   | SALESMAN | 7698 | 2013-01-02 | 1250.00 |  500.00 |     30 |
|  7654 | MARTIN | SALESMAN | 7698 | 2012-05-02 | 1250.00 | 1400.00 |     30 |
|  7698 | BLAKE  | MANAGER  | 7839 | 2012-01-06 | 2850.00 |    NULL |     30 |
|  7844 | TURNER | SALESMAN | 7698 | 2012-01-20 | 1500.00 |    0.00 |     30 |
|  7900 | JAMES  | CLERK    | 7698 | 2012-03-02 |  950.00 |    NULL |     30 |
+-------+--------+----------+------+------------+---------+---------+--------+
6 rows in set (0.01 sec)

mysql> select ename, empno,deptno from emp where job = 'clerk';
+--------+-------+--------+
| ename  | empno | deptno |
+--------+-------+--------+
| SMITH  |  7369 |     20 |
| ADAMS  |  7876 |     20 |
| JAMES  |  7900 |     30 |
| MILLER |  7934 |     10 |
+--------+-------+--------+
4 rows in set (0.00 sec)

mysql> select deptno,ename from emp where deptno >= 20;
+--------+--------+
| deptno | ename  |
+--------+--------+
|     20 | SMITH  |
|     30 | ALLEN  |
|     30 | WARD   |
|     20 | JONES  |
|     30 | MARTIN |
|     30 | BLAKE  |
|     20 | SCOTT  |
|     30 | TURNER |
|     20 | ADAMS  |
|     30 | JAMES  |
|     20 | FORD   |
+--------+--------+
11 rows in set (0.01 sec)

mysql> select empno,ename from emp where comm > sal;
+-------+--------+
| empno | ename  |
+-------+--------+
|  7654 | MARTIN |
+-------+--------+
1 row in set (0.00 sec)

mysql> select * from emp where comm > (60/100*sal);
+-------+--------+----------+------+------------+---------+---------+--------+
| EMPNO | ENAME  | JOB      | MGR  | HIREDATE   | SAL     | COMM    | DEPTNO |
+-------+--------+----------+------+------------+---------+---------+--------+
|  7654 | MARTIN | SALESMAN | 7698 | 2012-05-02 | 1250.00 | 1400.00 |     30 |
+-------+--------+----------+------+------------+---------+---------+--------+
1 row in set (0.00 sec)

mysql> select * from emp where comm > (50/100*sal);
+-------+--------+----------+------+------------+---------+---------+--------+
| EMPNO | ENAME  | JOB      | MGR  | HIREDATE   | SAL     | COMM    | DEPTNO |
+-------+--------+----------+------+------------+---------+---------+--------+
|  7654 | MARTIN | SALESMAN | 7698 | 2012-05-02 | 1250.00 | 1400.00 |     30 |
+-------+--------+----------+------+------------+---------+---------+--------+
1 row in set (0.00 sec)

mysql> select ename,job,sal from emp where deptno = 20 and sal > 2000;
+-------+---------+---------+
| ename | job     | sal     |
+-------+---------+---------+
| JONES | MANAGER | 2975.00 |
| SCOTT | ANALYST | 3000.00 |
| FORD  | ANALYST | 3000.00 |
+-------+---------+---------+
3 rows in set (0.00 sec)

mysql> select * from emp where deptno=30 and sal>=1500 and job='salesman';
+-------+--------+----------+------+------------+---------+--------+--------+
| EMPNO | ENAME  | JOB      | MGR  | HIREDATE   | SAL     | COMM   | DEPTNO |
+-------+--------+----------+------+------------+---------+--------+--------+
|  7499 | ALLEN  | SALESMAN | 7698 | 2012-01-02 | 1600.00 | 300.00 |     30 |
|  7844 | TURNER | SALESMAN | 7698 | 2012-01-20 | 1500.00 |   0.00 |     30 |
+-------+--------+----------+------+------------+---------+--------+--------+
2 rows in set (0.00 sec)

mysql> select * from emp where job ='president' or job ='manager';
+-------+-------+-----------+------+------------+---------+------+--------+
| EMPNO | ENAME | JOB       | MGR  | HIREDATE   | SAL     | COMM | DEPTNO |
+-------+-------+-----------+------+------------+---------+------+--------+
|  7566 | JONES | MANAGER   | 7839 | 2013-01-02 | 2975.00 | NULL |     20 |
|  7698 | BLAKE | MANAGER   | 7839 | 2012-01-06 | 2850.00 | NULL |     30 |
|  7782 | CLARK | MANAGER   | 7839 | 2012-01-06 | 2450.00 | NULL |     10 |
|  7839 | KING  | PRESIDENT | NULL | 2012-01-15 | 5000.00 | NULL |     10 |
+-------+-------+-----------+------+------------+---------+------+--------+
4 rows in set (0.00 sec)

mysql> select * from emp where deptno != 30;
+-------+--------+-----------+------+------------+---------+------+--------+
| EMPNO | ENAME  | JOB       | MGR  | HIREDATE   | SAL     | COMM | DEPTNO |
+-------+--------+-----------+------+------------+---------+------+--------+
|  7369 | SMITH  | CLERK     | 7902 | 2012-02-02 |  800.00 | NULL |     20 |
|  7566 | JONES  | MANAGER   | 7839 | 2013-01-02 | 2975.00 | NULL |     20 |
|  7782 | CLARK  | MANAGER   | 7839 | 2012-01-06 | 2450.00 | NULL |     10 |
|  7788 | SCOTT  | ANALYST   | 7566 | 2012-01-10 | 3000.00 | NULL |     20 |
|  7839 | KING   | PRESIDENT | NULL | 2012-01-15 | 5000.00 | NULL |     10 |
|  7876 | ADAMS  | CLERK     | 7788 | 2013-01-02 | 1100.00 | NULL |     20 |
|  7902 | FORD   | ANALYST   | 7566 | 2012-04-02 | 3000.00 | NULL |     20 |
|  7934 | MILLER | CLERK     | 7782 | 2012-05-02 | 1300.00 | NULL |     10 |
+-------+--------+-----------+------+------------+---------+------+--------+
8 rows in set (0.00 sec)

mysql> select * from emp where deptno != 30 and job ='manager';
+-------+-------+---------+------+------------+---------+------+--------+
| EMPNO | ENAME | JOB     | MGR  | HIREDATE   | SAL     | COMM | DEPTNO |
+-------+-------+---------+------+------------+---------+------+--------+
|  7566 | JONES | MANAGER | 7839 | 2013-01-02 | 2975.00 | NULL |     20 |
|  7782 | CLARK | MANAGER | 7839 | 2012-01-06 | 2450.00 | NULL |     10 |
+-------+-------+---------+------+------------+---------+------+--------+
2 rows in set (0.00 sec)

mysql> select * from emp where job = 'manager' or job='clerk' and deptno=10;
+-------+--------+---------+------+------------+---------+------+--------+
| EMPNO | ENAME  | JOB     | MGR  | HIREDATE   | SAL     | COMM | DEPTNO |
+-------+--------+---------+------+------------+---------+------+--------+
|  7566 | JONES  | MANAGER | 7839 | 2013-01-02 | 2975.00 | NULL |     20 |
|  7698 | BLAKE  | MANAGER | 7839 | 2012-01-06 | 2850.00 | NULL |     30 |
|  7782 | CLARK  | MANAGER | 7839 | 2012-01-06 | 2450.00 | NULL |     10 |
|  7934 | MILLER | CLERK   | 7782 | 2012-05-02 | 1300.00 | NULL |     10 |
+-------+--------+---------+------+------------+---------+------+--------+
4 rows in set (0.00 sec)

mysql> select * from emp where (job = 'manager' or job='clerk') and deptno=10;
+-------+--------+---------+------+------------+---------+------+--------+
| EMPNO | ENAME  | JOB     | MGR  | HIREDATE   | SAL     | COMM | DEPTNO |
+-------+--------+---------+------+------------+---------+------+--------+
|  7782 | CLARK  | MANAGER | 7839 | 2012-01-06 | 2450.00 | NULL |     10 |
|  7934 | MILLER | CLERK   | 7782 | 2012-05-02 | 1300.00 | NULL |     10 |
+-------+--------+---------+------+------------+---------+------+--------+
2 rows in set (0.00 sec)

mysql> select * from emp where job='manager' or (job='clerk' and deptno=10);
+-------+--------+---------+------+------------+---------+------+--------+
| EMPNO | ENAME  | JOB     | MGR  | HIREDATE   | SAL     | COMM | DEPTNO |
+-------+--------+---------+------+------------+---------+------+--------+
|  7566 | JONES  | MANAGER | 7839 | 2013-01-02 | 2975.00 | NULL |     20 |
|  7698 | BLAKE  | MANAGER | 7839 | 2012-01-06 | 2850.00 | NULL |     30 |
|  7782 | CLARK  | MANAGER | 7839 | 2012-01-06 | 2450.00 | NULL |     10 |
|  7934 | MILLER | CLERK   | 7782 | 2012-05-02 | 1300.00 | NULL |     10 |
+-------+--------+---------+------+------------+---------+------+--------+
4 rows in set (0.00 sec)

mysql> select * from emp where (job = 'manager' and deptno=10) or (job='clerk' and deptno=10);
+-------+--------+---------+------+------------+---------+------+--------+
| EMPNO | ENAME  | JOB     | MGR  | HIREDATE   | SAL     | COMM | DEPTNO |
+-------+--------+---------+------+------------+---------+------+--------+
|  7782 | CLARK  | MANAGER | 7839 | 2012-01-06 | 2450.00 | NULL |     10 |
|  7934 | MILLER | CLERK   | 7782 | 2012-05-02 | 1300.00 | NULL |     10 |
+-------+--------+---------+------+------------+---------+------+--------+
2 rows in set (0.00 sec)

mysql> select * from emp where (job = 'manager' and deptno=10) or (job='clerk' and deptno=20);
+-------+-------+---------+------+------------+---------+------+--------+
| EMPNO | ENAME | JOB     | MGR  | HIREDATE   | SAL     | COMM | DEPTNO |
+-------+-------+---------+------+------------+---------+------+--------+
|  7369 | SMITH | CLERK   | 7902 | 2012-02-02 |  800.00 | NULL |     20 |
|  7782 | CLARK | MANAGER | 7839 | 2012-01-06 | 2450.00 | NULL |     10 |
|  7876 | ADAMS | CLERK   | 7788 | 2013-01-02 | 1100.00 | NULL |     20 |
+-------+-------+---------+------+------------+---------+------+--------+
3 rows in set (0.00 sec)

mysql> select * from emp where (job!='clerk' or job!='manager') and sal >= 2000;
+-------+-------+-----------+------+------------+---------+------+--------+
| EMPNO | ENAME | JOB       | MGR  | HIREDATE   | SAL     | COMM | DEPTNO |
+-------+-------+-----------+------+------------+---------+------+--------+
|  7566 | JONES | MANAGER   | 7839 | 2013-01-02 | 2975.00 | NULL |     20 |
|  7698 | BLAKE | MANAGER   | 7839 | 2012-01-06 | 2850.00 | NULL |     30 |
|  7782 | CLARK | MANAGER   | 7839 | 2012-01-06 | 2450.00 | NULL |     10 |
|  7788 | SCOTT | ANALYST   | 7566 | 2012-01-10 | 3000.00 | NULL |     20 |
|  7839 | KING  | PRESIDENT | NULL | 2012-01-15 | 5000.00 | NULL |     10 |
|  7902 | FORD  | ANALYST   | 7566 | 2012-04-02 | 3000.00 | NULL |     20 |
+-------+-------+-----------+------+------------+---------+------+--------+
6 rows in set (0.00 sec)

mysql> select ename from emp where (job!='clerk' or job!='manager');
+--------+
| ename  |
+--------+
| SMITH  |
| ALLEN  |
| WARD   |
| JONES  |
| MARTIN |
| BLAKE  |
| CLARK  |
| SCOTT  |
| KING   |
| TURNER |
| ADAMS  |
| JAMES  |
| FORD   |
| MILLER |
+--------+
14 rows in set (0.00 sec)

mysql> select * from emp where sal between 1200 and 1400
    -> ;
+-------+--------+----------+------+------------+---------+---------+--------+
| EMPNO | ENAME  | JOB      | MGR  | HIREDATE   | SAL     | COMM    | DEPTNO |
+-------+--------+----------+------+------------+---------+---------+--------+
|  7521 | WARD   | SALESMAN | 7698 | 2013-01-02 | 1250.00 |  500.00 |     30 |
|  7654 | MARTIN | SALESMAN | 7698 | 2012-05-02 | 1250.00 | 1400.00 |     30 |
|  7934 | MILLER | CLERK    | 7782 | 2012-05-02 | 1300.00 |    NULL |     10 |
+-------+--------+----------+------+------------+---------+---------+--------+
3 rows in set (0.01 sec)

mysql> select ename from emp where (job!='clerk' or job!='manager') and deptno=20;
+-------+
| ename |
+-------+
| SMITH |
| JONES |
| SCOTT |
| ADAMS |
| FORD  |
+-------+
5 rows in set (0.00 sec)

mysql> select * from emp where (job!='clerk' or job!='manager') and deptno=20;
+-------+-------+---------+------+------------+---------+------+--------+
| EMPNO | ENAME | JOB     | MGR  | HIREDATE   | SAL     | COMM | DEPTNO |
+-------+-------+---------+------+------------+---------+------+--------+
|  7369 | SMITH | CLERK   | 7902 | 2012-02-02 |  800.00 | NULL |     20 |
|  7566 | JONES | MANAGER | 7839 | 2013-01-02 | 2975.00 | NULL |     20 |
|  7788 | SCOTT | ANALYST | 7566 | 2012-01-10 | 3000.00 | NULL |     20 |
|  7876 | ADAMS | CLERK   | 7788 | 2013-01-02 | 1100.00 | NULL |     20 |
|  7902 | FORD  | ANALYST | 7566 | 2012-04-02 | 3000.00 | NULL |     20 |
+-------+-------+---------+------+------------+---------+------+--------+
5 rows in set (0.00 sec)

mysql> select * from emp where (job!='clerk' and job!='manager') and deptno=20;
+-------+-------+---------+------+------------+---------+------+--------+
| EMPNO | ENAME | JOB     | MGR  | HIREDATE   | SAL     | COMM | DEPTNO |
+-------+-------+---------+------+------------+---------+------+--------+
|  7788 | SCOTT | ANALYST | 7566 | 2012-01-10 | 3000.00 | NULL |     20 |
|  7902 | FORD  | ANALYST | 7566 | 2012-04-02 | 3000.00 | NULL |     20 |
+-------+-------+---------+------+------------+---------+------+--------+
2 rows in set (0.00 sec)

mysql> select * from emp where sal between 1200 and 1400
    -> ;
+-------+--------+----------+------+------------+---------+---------+--------+
| EMPNO | ENAME  | JOB      | MGR  | HIREDATE   | SAL     | COMM    | DEPTNO |
+-------+--------+----------+------+------------+---------+---------+--------+
|  7521 | WARD   | SALESMAN | 7698 | 2013-01-02 | 1250.00 |  500.00 |     30 |
|  7654 | MARTIN | SALESMAN | 7698 | 2012-05-02 | 1250.00 | 1400.00 |     30 |
|  7934 | MILLER | CLERK    | 7782 | 2012-05-02 | 1300.00 |    NULL |     10 |
+-------+--------+----------+------+------------+---------+---------+--------+
3 rows in set (0.00 sec)

mysql> select * from emp where job= 'clerk' or job= 'analyst' or job='salesman';
+-------+--------+----------+------+------------+---------+---------+--------+
| EMPNO | ENAME  | JOB      | MGR  | HIREDATE   | SAL     | COMM    | DEPTNO |
+-------+--------+----------+------+------------+---------+---------+--------+
|  7369 | SMITH  | CLERK    | 7902 | 2012-02-02 |  800.00 |    NULL |     20 |
|  7499 | ALLEN  | SALESMAN | 7698 | 2012-01-02 | 1600.00 |  300.00 |     30 |
|  7521 | WARD   | SALESMAN | 7698 | 2013-01-02 | 1250.00 |  500.00 |     30 |
|  7654 | MARTIN | SALESMAN | 7698 | 2012-05-02 | 1250.00 | 1400.00 |     30 |
|  7788 | SCOTT  | ANALYST  | 7566 | 2012-01-10 | 3000.00 |    NULL |     20 |
|  7844 | TURNER | SALESMAN | 7698 | 2012-01-20 | 1500.00 |    0.00 |     30 |
|  7876 | ADAMS  | CLERK    | 7788 | 2013-01-02 | 1100.00 |    NULL |     20 |
|  7900 | JAMES  | CLERK    | 7698 | 2012-03-02 |  950.00 |    NULL |     30 |
|  7902 | FORD   | ANALYST  | 7566 | 2012-04-02 | 3000.00 |    NULL |     20 |
|  7934 | MILLER | CLERK    | 7782 | 2012-05-02 | 1300.00 |    NULL |     10 |
+-------+--------+----------+------+------------+---------+---------+--------+
10 rows in set (0.00 sec)

mysql> select * from emp where job!= 'clerk' or job!= 'analyst' or job!='salesman';
+-------+--------+-----------+------+------------+---------+---------+--------+
| EMPNO | ENAME  | JOB       | MGR  | HIREDATE   | SAL     | COMM    | DEPTNO |
+-------+--------+-----------+------+------------+---------+---------+--------+
|  7369 | SMITH  | CLERK     | 7902 | 2012-02-02 |  800.00 |    NULL |     20 |
|  7499 | ALLEN  | SALESMAN  | 7698 | 2012-01-02 | 1600.00 |  300.00 |     30 |
|  7521 | WARD   | SALESMAN  | 7698 | 2013-01-02 | 1250.00 |  500.00 |     30 |
|  7566 | JONES  | MANAGER   | 7839 | 2013-01-02 | 2975.00 |    NULL |     20 |
|  7654 | MARTIN | SALESMAN  | 7698 | 2012-05-02 | 1250.00 | 1400.00 |     30 |
|  7698 | BLAKE  | MANAGER   | 7839 | 2012-01-06 | 2850.00 |    NULL |     30 |
|  7782 | CLARK  | MANAGER   | 7839 | 2012-01-06 | 2450.00 |    NULL |     10 |
|  7788 | SCOTT  | ANALYST   | 7566 | 2012-01-10 | 3000.00 |    NULL |     20 |
|  7839 | KING   | PRESIDENT | NULL | 2012-01-15 | 5000.00 |    NULL |     10 |
|  7844 | TURNER | SALESMAN  | 7698 | 2012-01-20 | 1500.00 |    0.00 |     30 |
|  7876 | ADAMS  | CLERK     | 7788 | 2013-01-02 | 1100.00 |    NULL |     20 |
|  7900 | JAMES  | CLERK     | 7698 | 2012-03-02 |  950.00 |    NULL |     30 |
|  7902 | FORD   | ANALYST   | 7566 | 2012-04-02 | 3000.00 |    NULL |     20 |
|  7934 | MILLER | CLERK     | 7782 | 2012-05-02 | 1300.00 |    NULL |     10 |
+-------+--------+-----------+------+------------+---------+---------+--------+
14 rows in set (0.00 sec)

mysql> select * from emp where comm=NULL;
Empty set (0.00 sec)

mysql> select * from emp where comm= 'NULL';
+-------+--------+----------+------+------------+---------+------+--------+
| EMPNO | ENAME  | JOB      | MGR  | HIREDATE   | SAL     | COMM | DEPTNO |
+-------+--------+----------+------+------------+---------+------+--------+
|  7844 | TURNER | SALESMAN | 7698 | 2012-01-20 | 1500.00 | 0.00 |     30 |
+-------+--------+----------+------+------------+---------+------+--------+
1 row in set, 1 warning (0.01 sec)

mysql> select * from emp where comm IS NULL;
+-------+--------+-----------+------+------------+---------+------+--------+
| EMPNO | ENAME  | JOB       | MGR  | HIREDATE   | SAL     | COMM | DEPTNO |
+-------+--------+-----------+------+------------+---------+------+--------+
|  7369 | SMITH  | CLERK     | 7902 | 2012-02-02 |  800.00 | NULL |     20 |
|  7566 | JONES  | MANAGER   | 7839 | 2013-01-02 | 2975.00 | NULL |     20 |
|  7698 | BLAKE  | MANAGER   | 7839 | 2012-01-06 | 2850.00 | NULL |     30 |
|  7782 | CLARK  | MANAGER   | 7839 | 2012-01-06 | 2450.00 | NULL |     10 |
|  7788 | SCOTT  | ANALYST   | 7566 | 2012-01-10 | 3000.00 | NULL |     20 |
|  7839 | KING   | PRESIDENT | NULL | 2012-01-15 | 5000.00 | NULL |     10 |
|  7876 | ADAMS  | CLERK     | 7788 | 2013-01-02 | 1100.00 | NULL |     20 |
|  7900 | JAMES  | CLERK     | 7698 | 2012-03-02 |  950.00 | NULL |     30 |
|  7902 | FORD   | ANALYST   | 7566 | 2012-04-02 | 3000.00 | NULL |     20 |
|  7934 | MILLER | CLERK     | 7782 | 2012-05-02 | 1300.00 | NULL |     10 |
+-------+--------+-----------+------+------------+---------+------+--------+
10 rows in set (0.00 sec)

mysql> select * from emp where comm = 0.00;
+-------+--------+----------+------+------------+---------+------+--------+
| EMPNO | ENAME  | JOB      | MGR  | HIREDATE   | SAL     | COMM | DEPTNO |
+-------+--------+----------+------+------------+---------+------+--------+
|  7844 | TURNER | SALESMAN | 7698 | 2012-01-20 | 1500.00 | 0.00 |     30 |
+-------+--------+----------+------+------------+---------+------+--------+
1 row in set (0.00 sec)

mysql> select * from emp;
+-------+--------+-----------+------+------------+---------+---------+--------+
| EMPNO | ENAME  | JOB       | MGR  | HIREDATE   | SAL     | COMM    | DEPTNO |
+-------+--------+-----------+------+------------+---------+---------+--------+
|  7369 | SMITH  | CLERK     | 7902 | 2012-02-02 |  800.00 |    NULL |     20 |
|  7499 | ALLEN  | SALESMAN  | 7698 | 2012-01-02 | 1600.00 |  300.00 |     30 |
|  7521 | WARD   | SALESMAN  | 7698 | 2013-01-02 | 1250.00 |  500.00 |     30 |
|  7566 | JONES  | MANAGER   | 7839 | 2013-01-02 | 2975.00 |    NULL |     20 |
|  7654 | MARTIN | SALESMAN  | 7698 | 2012-05-02 | 1250.00 | 1400.00 |     30 |
|  7698 | BLAKE  | MANAGER   | 7839 | 2012-01-06 | 2850.00 |    NULL |     30 |
|  7782 | CLARK  | MANAGER   | 7839 | 2012-01-06 | 2450.00 |    NULL |     10 |
|  7788 | SCOTT  | ANALYST   | 7566 | 2012-01-10 | 3000.00 |    NULL |     20 |
|  7839 | KING   | PRESIDENT | NULL | 2012-01-15 | 5000.00 |    NULL |     10 |
|  7844 | TURNER | SALESMAN  | 7698 | 2012-01-20 | 1500.00 |    0.00 |     30 |
|  7876 | ADAMS  | CLERK     | 7788 | 2013-01-02 | 1100.00 |    NULL |     20 |
|  7900 | JAMES  | CLERK     | 7698 | 2012-03-02 |  950.00 |    NULL |     30 |
|  7902 | FORD   | ANALYST   | 7566 | 2012-04-02 | 3000.00 |    NULL |     20 |
|  7934 | MILLER | CLERK     | 7782 | 2012-05-02 | 1300.00 |    NULL |     10 |
+-------+--------+-----------+------+------------+---------+---------+--------+
14 rows in set (0.00 sec)

mysql> select distinct(job)  from emp where comm is not null;
+----------+
| job      |
+----------+
| SALESMAN |
+----------+
1 row in set (0.01 sec)

mysql> select * from emp where comm is null or comm <100;
+-------+--------+-----------+------+------------+---------+------+--------+
| EMPNO | ENAME  | JOB       | MGR  | HIREDATE   | SAL     | COMM | DEPTNO |
+-------+--------+-----------+------+------------+---------+------+--------+
|  7369 | SMITH  | CLERK     | 7902 | 2012-02-02 |  800.00 | NULL |     20 |
|  7566 | JONES  | MANAGER   | 7839 | 2013-01-02 | 2975.00 | NULL |     20 |
|  7698 | BLAKE  | MANAGER   | 7839 | 2012-01-06 | 2850.00 | NULL |     30 |
|  7782 | CLARK  | MANAGER   | 7839 | 2012-01-06 | 2450.00 | NULL |     10 |
|  7788 | SCOTT  | ANALYST   | 7566 | 2012-01-10 | 3000.00 | NULL |     20 |
|  7839 | KING   | PRESIDENT | NULL | 2012-01-15 | 5000.00 | NULL |     10 |
|  7844 | TURNER | SALESMAN  | 7698 | 2012-01-20 | 1500.00 | 0.00 |     30 |
|  7876 | ADAMS  | CLERK     | 7788 | 2013-01-02 | 1100.00 | NULL |     20 |
|  7900 | JAMES  | CLERK     | 7698 | 2012-03-02 |  950.00 | NULL |     30 |
|  7902 | FORD   | ANALYST   | 7566 | 2012-04-02 | 3000.00 | NULL |     20 |
|  7934 | MILLER | CLERK     | 7782 | 2012-05-02 | 1300.00 | NULL |     10 |
+-------+--------+-----------+------+------------+---------+------+--------+
11 rows in set (0.00 sec)

mysql> select * from emp where ename like 'm%'
    -> ;
+-------+--------+----------+------+------------+---------+---------+--------+
| EMPNO | ENAME  | JOB      | MGR  | HIREDATE   | SAL     | COMM    | DEPTNO |
+-------+--------+----------+------+------------+---------+---------+--------+
|  7654 | MARTIN | SALESMAN | 7698 | 2012-05-02 | 1250.00 | 1400.00 |     30 |
|  7934 | MILLER | CLERK    | 7782 | 2012-05-02 | 1300.00 |    NULL |     10 |
+-------+--------+----------+------+------------+---------+---------+--------+
2 rows in set (0.00 sec)

mysql> select * from emp where ename like '%m%' or ename like '%M%';
+-------+--------+----------+------+------------+---------+---------+--------+
| EMPNO | ENAME  | JOB      | MGR  | HIREDATE   | SAL     | COMM    | DEPTNO |
+-------+--------+----------+------+------------+---------+---------+--------+
|  7369 | SMITH  | CLERK    | 7902 | 2012-02-02 |  800.00 |    NULL |     20 |
|  7654 | MARTIN | SALESMAN | 7698 | 2012-05-02 | 1250.00 | 1400.00 |     30 |
|  7876 | ADAMS  | CLERK    | 7788 | 2013-01-02 | 1100.00 |    NULL |     20 |
|  7900 | JAMES  | CLERK    | 7698 | 2012-03-02 |  950.00 |    NULL |     30 |
|  7934 | MILLER | CLERK    | 7782 | 2012-05-02 | 1300.00 |    NULL |     10 |
+-------+--------+----------+------+------------+---------+---------+--------+
5 rows in set (0.00 sec)

mysql> select * from emp where ename like '____n';
+-------+-------+----------+------+------------+---------+--------+--------+
| EMPNO | ENAME | JOB      | MGR  | HIREDATE   | SAL     | COMM   | DEPTNO |
+-------+-------+----------+------+------------+---------+--------+--------+
|  7499 | ALLEN | SALESMAN | 7698 | 2012-01-02 | 1600.00 | 300.00 |     30 |
+-------+-------+----------+------+------------+---------+--------+--------+
1 row in set (0.00 sec)

mysql> select * from emp where ename like '__r%';
+-------+--------+----------+------+------------+---------+---------+--------+
| EMPNO | ENAME  | JOB      | MGR  | HIREDATE   | SAL     | COMM    | DEPTNO |
+-------+--------+----------+------+------------+---------+---------+--------+
|  7521 | WARD   | SALESMAN | 7698 | 2013-01-02 | 1250.00 |  500.00 |     30 |
|  7654 | MARTIN | SALESMAN | 7698 | 2012-05-02 | 1250.00 | 1400.00 |     30 |
|  7844 | TURNER | SALESMAN | 7698 | 2012-01-20 | 1500.00 |    0.00 |     30 |
|  7902 | FORD   | ANALYST  | 7566 | 2012-04-02 | 3000.00 |    NULL |     20 |
+-------+--------+----------+------+------------+---------+---------+--------+
4 rows in set (0.00 sec)

mysql> select * from emp where month(hiredate) = 02;
+-------+-------+-------+------+------------+--------+------+--------+
| EMPNO | ENAME | JOB   | MGR  | HIREDATE   | SAL    | COMM | DEPTNO |
+-------+-------+-------+------+------------+--------+------+--------+
|  7369 | SMITH | CLERK | 7902 | 2012-02-02 | 800.00 | NULL |     20 |
+-------+-------+-------+------+------------+--------+------+--------+
1 row in set (0.01 sec)

mysql> select * from emp;
+-------+--------+-----------+------+------------+---------+---------+--------+
| EMPNO | ENAME  | JOB       | MGR  | HIREDATE   | SAL     | COMM    | DEPTNO |
+-------+--------+-----------+------+------------+---------+---------+--------+
|  7369 | SMITH  | CLERK     | 7902 | 2012-02-02 |  800.00 |    NULL |     20 |
|  7499 | ALLEN  | SALESMAN  | 7698 | 2012-01-02 | 1600.00 |  300.00 |     30 |
|  7521 | WARD   | SALESMAN  | 7698 | 2013-01-02 | 1250.00 |  500.00 |     30 |
|  7566 | JONES  | MANAGER   | 7839 | 2013-01-02 | 2975.00 |    NULL |     20 |
|  7654 | MARTIN | SALESMAN  | 7698 | 2012-05-02 | 1250.00 | 1400.00 |     30 |
|  7698 | BLAKE  | MANAGER   | 7839 | 2012-01-06 | 2850.00 |    NULL |     30 |
|  7782 | CLARK  | MANAGER   | 7839 | 2012-01-06 | 2450.00 |    NULL |     10 |
|  7788 | SCOTT  | ANALYST   | 7566 | 2012-01-10 | 3000.00 |    NULL |     20 |
|  7839 | KING   | PRESIDENT | NULL | 2012-01-15 | 5000.00 |    NULL |     10 |
|  7844 | TURNER | SALESMAN  | 7698 | 2012-01-20 | 1500.00 |    0.00 |     30 |
|  7876 | ADAMS  | CLERK     | 7788 | 2013-01-02 | 1100.00 |    NULL |     20 |
|  7900 | JAMES  | CLERK     | 7698 | 2012-03-02 |  950.00 |    NULL |     30 |
|  7902 | FORD   | ANALYST   | 7566 | 2012-04-02 | 3000.00 |    NULL |     20 |
|  7934 | MILLER | CLERK     | 7782 | 2012-05-02 | 1300.00 |    NULL |     10 |
+-------+--------+-----------+------+------------+---------+---------+--------+
14 rows in set (0.00 sec)

mysql> select * from emp where year(hiredate) = 2012  and job='manager';
+-------+-------+---------+------+------------+---------+------+--------+
| EMPNO | ENAME | JOB     | MGR  | HIREDATE   | SAL     | COMM | DEPTNO |
+-------+-------+---------+------+------------+---------+------+--------+
|  7698 | BLAKE | MANAGER | 7839 | 2012-01-06 | 2850.00 | NULL |     30 |
|  7782 | CLARK | MANAGER | 7839 | 2012-01-06 | 2450.00 | NULL |     10 |
+-------+-------+---------+------+------------+---------+------+--------+
2 rows in set (0.00 sec)

mysql> select ename from emp where ename like 'a%';
+-------+
| ename |
+-------+
| ALLEN |
| ADAMS |
+-------+
2 rows in set (0.00 sec)

mysql> select ename from emp where ename like '%a%';
+--------+
| ename  |
+--------+
| ALLEN  |
| WARD   |
| MARTIN |
| BLAKE  |
| CLARK  |
| ADAMS  |
| JAMES  |
+--------+
7 rows in set (0.00 sec)

mysql> select * from emp;
+-------+--------+-----------+------+------------+---------+---------+--------+
| EMPNO | ENAME  | JOB       | MGR  | HIREDATE   | SAL     | COMM    | DEPTNO |
+-------+--------+-----------+------+------------+---------+---------+--------+
|  7369 | SMITH  | CLERK     | 7902 | 2012-02-02 |  800.00 |    NULL |     20 |
|  7499 | ALLEN  | SALESMAN  | 7698 | 2012-01-02 | 1600.00 |  300.00 |     30 |
|  7521 | WARD   | SALESMAN  | 7698 | 2013-01-02 | 1250.00 |  500.00 |     30 |
|  7566 | JONES  | MANAGER   | 7839 | 2013-01-02 | 2975.00 |    NULL |     20 |
|  7654 | MARTIN | SALESMAN  | 7698 | 2012-05-02 | 1250.00 | 1400.00 |     30 |
|  7698 | BLAKE  | MANAGER   | 7839 | 2012-01-06 | 2850.00 |    NULL |     30 |
|  7782 | CLARK  | MANAGER   | 7839 | 2012-01-06 | 2450.00 |    NULL |     10 |
|  7788 | SCOTT  | ANALYST   | 7566 | 2012-01-10 | 3000.00 |    NULL |     20 |
|  7839 | KING   | PRESIDENT | NULL | 2012-01-15 | 5000.00 |    NULL |     10 |
|  7844 | TURNER | SALESMAN  | 7698 | 2012-01-20 | 1500.00 |    0.00 |     30 |
|  7876 | ADAMS  | CLERK     | 7788 | 2013-01-02 | 1100.00 |    NULL |     20 |
|  7900 | JAMES  | CLERK     | 7698 | 2012-03-02 |  950.00 |    NULL |     30 |
|  7902 | FORD   | ANALYST   | 7566 | 2012-04-02 | 3000.00 |    NULL |     20 |
|  7934 | MILLER | CLERK     | 7782 | 2012-05-02 | 1300.00 |    NULL |     10 |
+-------+--------+-----------+------+------------+---------+---------+--------+
14 rows in set (0.00 sec)

mysql> exit;
