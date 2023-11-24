# 175题
``` mysql
select FirstName, LastName, City, State
from Person left join Address
on Person.PersonId = Address.PersonId
```

# 181题

``` mysql
SELECT
    a.name Employee
FROM
    Employee AS a,
    Employee AS b
WHERE
    a.ManagerId = b.Id
        AND a.Salary > b.Salary
```

# 182题

``` mysql
select DISTINCT  email 
from Person 
group by email
having count(email)> 1
```

# 183题
``` mysql
<!-- 方法一 -->
select  a.name as Customers
from  Customers a
left join Orders b
on a.id = b.customerId
where b.customerId  is NULl

<!-- 方法二 -->
select name as Customers
from Customers
where id not in (
    select customerId  from Orders
)
```

# 196题
``` mysql
delete p1.* from Person p1,Person p2 where p1.Email = p2.Email and p1.id> p2.id
```

# 197题
``` mysql
SELECT
	a.id 
FROM
	Weather  a
	CROSS JOIN Weather b
    on  DATEDIFF(a.recordDate , b.recordDate) = 1
WHERe  a.Temperature  > b.Temperature
```

# 511题
``` mysql
SELECT
  A.player_id,
    MIN(A.event_date) AS first_login
FROM
  Activity A
GROUP BY
  A.player_id;
```

# 577题
``` mysql
select a.name,b.Bonus
from Employee a
left join Bonus b 
on a.empId = b.empId
where b.Bonus < 1000 or b.Bonus is null
```

# 584题
``` mysql
SELECT name FROM customer WHERE referee_id != 2 OR referee_id IS NULL;
```

# 586题
``` mysql
select  customer_number
from Orders 
group by customer_number
order by count(customer_number) desc
limit 1
```

# 595题
``` mysql
SELECT 
    name, population, area 
FROM 
    world 
WHERE 
    area >= 3000000 
    OR population >= 25000000
```

# 596题
``` mysql
select class
from 
Courses
group by class  
having count(student) >= 5
```

# 607题
``` mysql
SELECT
    s.name
FROM
    salesperson s
WHERE
    s.sales_id NOT IN (SELECT
            c.sales_id
        FROM
            Company  o
                inner JOIN
            Orders  c ON o.com_id = c.com_id
        WHERE
            o.name = 'RED')
```

# 619题
``` mysql
select max(a.num) as num from
(
  select  num 
from MyNumbers 
group by num
having count(num) = 1
) a 
```

# 610题
``` mysql
SELECT 
    x,
    y,
    z,
    CASE
        WHEN x + y > z AND x + z > y AND y + z > x THEN 'Yes'
        ELSE 'No'
    END AS 'triangle'
FROM
    triangle
```

# 620题
``` mysql
select *
from cinema
where mod(id, 2) = 1 and description <> 'boring'
order by rating DESC
```


# 627题
``` mysql
UPDATE salary
SET
    sex = CASE sex
        WHEN 'm' THEN 'f'
        ELSE 'm'
    END;
```

# 1050题
``` mysql
SELECT actor_id, director_id
FROM ActorDirector
GROUP BY actor_id, director_id
HAVING COUNT(timestamp) >= 3;
```

# 1068题
``` mysql
select 
	p.product_name,
	s.year,
	s.price
from Sales s 
left join Product p
on s.product_id=p.product_id
```

# 1075题
``` mysql
SELECT
    project_id,
    ROUND(AVG(e.experience_years),2)  AS average_years
FROM
    Project as p 
LEFT JOIN
    Employee as e
ON
    p.employee_id = e.employee_id
GROUP BY
    p.project_id
```

# 1084题
``` mysql
select product_id,product_name   from  product where 
product_id in (select  product_id
FROM Sales
group by product_id
having max(sale_date)<= '2019-03-31' and  min(sale_date)>='2019-01-01')
```


# 1141题
``` mysql
select activity_date AS day,
    COUNT(DISTINCT user_id) AS active_users from Activity
where datediff('2019-7-27',activity_date) < 30
and activity_date <= '2019-07-27'
group by activity_date 
```


# 1148题
``` mysql
select distinct
author_id  as id
from views
where author_id = viewer_id order by author_id
```

# 1179题 (有趣)

``` mysql
select 
id, 
sum(case when month = 'Jan' then revenue end) as Jan_Revenue,
sum(case when month = 'Feb' then revenue end) as Feb_Revenue,
sum(case when month = 'Mar' then revenue end) as Mar_Revenue,
sum(case when month = 'Apr' then revenue end) as Apr_Revenue,
sum(case when month = 'May' then revenue end) as May_Revenue,
sum(case when month = 'Jun' then revenue end) as Jun_Revenue,
sum(case when month = 'Jul' then revenue end) as Jul_Revenue,
sum(case when month = 'Aug' then revenue end) as Aug_Revenue,
sum(case when month = 'Sep' then revenue end) as Sep_Revenue,
sum(case when month = 'Oct' then revenue end) as Oct_Revenue,
sum(case when month = 'Nov' then revenue end) as Nov_Revenue,
sum(case when month = 'Dec' then revenue end) as Dec_Revenue
from 
Department
group by id
```


# 1211题
``` mysql
select distinct
    query_name,
   Round(AVG(rating / position),2) as quality ,
   Round(sum(if(rating< 3,1,0))/ count(*) * 100,2) as  poor_query_percentage
from Queries 
group by query_name 
```


# 1251题
``` mysql
// 写法一
select 
a.product_id, IFNULL(round(sum(a.price * b.units) / sum(units),2), 0) as average_price  
from 
Prices a 
left join 
UnitsSold b
on a.product_id = b.product_id
where b.purchase_date between start_date and end_date   or  b.purchase_date is null   
group by a.product_id

// 写法二
select 
a.product_id, IFNULL(round(sum(a.price * b.units) / sum(units),2), 0) as average_price  
from 
Prices a 
left join 
UnitsSold b
<!-- 在on中写条件，没有的数据不会被过滤掉 -->
on a.product_id = b.product_id and b.purchase_date between start_date and end_date  
group by a.product_id  
```

# 1280题

``` mysql
select aa.student_id , aa.student_name,aa.subject_name , ifnull(count(cc.subject_name),0)  as attended_exams 
from
(select * 
from Students  a cross join  Subjects  b) aa 
left join Examinations cc 
on aa.student_id  = cc.student_id and aa.subject_name  = cc.subject_name 
group by aa.student_id,aa.subject_name 
order by aa.student_id
```

# 1327题

``` mysql
select  product_name, sum(unit) as unit 
from
(select a.product_id, a.product_name ,date_format(b.order_date,'%Y-%m' ) as order_date,b.unit  from 
Products a 
left join 
Orders b
on a.product_id  = b.product_id) aa
where order_date = '2020-02'
group by aa.product_id ,aa.order_date
having sum(unit) >= 100
```

# 1378题

``` mysql
select b.unique_id , a.name from 
Employees a 
left join EmployeeUNI  b
on a.id = b.id
```

# 1407题

``` mysql
select * from
(select a.name ,ifnull(sum(b.distance) ,0)  as travelled_distance
from Users a 
left join Rides b
on a.id = b.user_id
group by user_id) aa
order by aa.travelled_distance desc ,aa.name
```

# 1484题

``` mysql
select  sell_date, count(sell_date) as num_sold, GROUP_CONCAT(distinct product SEPARATOR ',') as products
from
(select distinct * from
Activities order by product) a
group by sell_date
order by sell_date 
```

# 1517题

``` mysql
SELECT user_id, name, mail
FROM Users
# 对`@`字符进行了转义
WHERE mail REGEXP '^[a-zA-Z][a-zA-Z0-9_.-]*\\@leetcode\\.com$';
```

# 1527题

``` mysql
select  *
from Patients
where  conditions  like '% DIAB1%' or conditions  like 'DIAB1%'
```


# 1581题
``` mysql
select customer_id,count(customer_id ) as  count_no_trans  from Visits
where visit_id  not in (select visit_id from Transactions )
group by customer_id 
```

# 1587题

``` mysql
select  a.name , sum(amount) as BALANCE 
from Users  a
left join 
Transactions b
on a.account = b.account
group by a.account 
having  sum(amount)> 10000
```

# 1633题

``` mysql
### 方法一
select 
aaa.contest_id ,round(count(bbb.contest_id ) / count(aaa.user_name)  * 100,2) as percentage 
from
# 找到赛事可报名的所有人
(select * from
# 找到所有的赛事
(select contest_id
from  Register
group by contest_id ) aa 
cross join 
Users bb) aaa
left join Register bbb
on aaa.user_id  = bbb.user_id and aaa.contest_id = bbb.contest_id 
group by aaa.contest_id
order by percentage desc,contest_id 

### 方法二 
select contest_id,round(100*count(user_id)/
(   select 
    count(user_id)
    from Users)
,2) percentage
from Register R 
group by contest_id
order by percentage desc,contest_id
```

# 1661题

``` mysql
select machine_id ,round(sum(timestampout)/count(process_id),3) as processing_time from
(select  machine_id ,process_id  ,max(timestamp)-min(timestamp) as timestampout from Activity 
group by machine_id,process_id) a
group by machine_id
```

# 1683题

``` mysql
select  tweet_id 
from Tweets 
where char_length(content) > 15
```

# 1693题

``` mysql
select date_id,make_name , count(distinct lead_id)as unique_leads ,count(distinct partner_id )as unique_partners  from 
DailySales
group by date_id,make_name 
```

# 1729题

``` mysql
select user_id ,count(distinct follower_id) as followers_count   from 
Followers
group by user_id
```


# 1731题
``` mysql
select a.reports_to as employee_id ,b.name ,count(a.name) as reports_count ,round(avg(a.age)) as average_age  from
Employees a 
inner join Employees b
on a.reports_to = b.Employee_id
group by b.employee_id
order by b.employee_id 
```

# 1741题

``` mysql
select  event_day  as day,emp_id ,sum(resive_time) as total_time  from 
(select *,(out_time-in_time ) as resive_time from 
Employees) a
group by emp_id,event_day 
```

# 1757题

``` mysql
select product_id   from 
Products
where low_fats = 'Y' and recyclable = 'Y'
```

# 1789题

``` mysql
select employee_id ,department_id from Employee  
where primary_flag = 'Y'
union
select employee_id ,department_id  from Employee 
where  employee_id not in (
    select employee_id  from Employee  
where primary_flag = 'Y'
)
group by employee_id
having count(employee_id) = 1
```

# 1795题

``` mysql
#行转列 select后用UNION
#列转行 if/case,记得要MAX/SUM
SELECT product_id, 'store1' AS store, store1 AS price 
FROM Products 
WHERE store1 IS NOT NULL

UNION 
SELECT product_id, 'store2' AS store, store2 AS price 
FROM Products 
WHERE store2 IS NOT NULL

UNION 
SELECT product_id, 'store3' AS store, store3 AS price 
FROM Products 
WHERE store3 IS NOT NULL
```

# 1890题

``` mysql
select user_id,max(time_stamp) as last_stamp    from logins 
where time_stamp like "2020%"
group by  user_id 

```

# 1965题

``` mysql
select employee_id  from Employees 
where employee_id not in (select employee_id from salaries)
union
select employee_id  from salaries 
where employee_id not in (select employee_id from Employees)
order by employee_id 	
```

# 题

``` mysql

```

# 题

``` mysql

```


# 题
``` mysql

```


# 题
``` mysql

```


# 题
``` mysql

```


# 题
``` mysql

```