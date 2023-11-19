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


# 题
``` mysql

```