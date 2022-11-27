## 1

https://sql-ex.ru/learn_exercises.php?LN=1

```SELECT model, speed, hd FROM PC WHERE price < 500```

## 2

https://sql-ex.ru/learn_exercises.php?LN=2

```Select maker  from  product where product.type = 'printer' group by maker```

## 3
https://sql-ex.ru/learn_exercises.php?LN=3

```select * from printer where color = 'y'```

## 4
https://sql-ex.ru/learn_exercises.php?LN=4

```select * from printer where color = 'y'```

## 5
https://sql-ex.ru/learn_exercises.php?LN=5

```Select model ,speed , hd  from pc where (cd = '12x' or cd = '24x') and price < 600```

## 6

https://sql-ex.ru/learn_exercises.php?LN=6


```Select maker, speed  from Product inner join Laptop on Product.model = Laptop.model where hd >= 10```

## 7
https://sql-ex.ru/learn_exercises.php?LN=7

```
Select laptop.model , laptop.price  from laptop inner join product on laptop.model = product.model  
where product.maker= 'B' 
union 
Select pc.model , pc.price from pc inner join product on pc.model = product.model  
where product.maker= 'B' 
union 
Select printer.model , printer.price from printer inner join product on printer.model = product.model  
where product.maker= 'B'
```

## 8
https://sql-ex.ru/learn_exercises.php?LN=8

```
select maker from product where type='PC' and maker not in   
( select maker from product where type = 'Laptop') group by maker
```

## 9
https://sql-ex.ru/learn_exercises.php?LN=9

```
Select maker  from pc inner join product on pc.model = product.model where speed >= 450 
group by maker
```

## 10
https://sql-ex.ru/learn_exercises.php?LN=10

```
select model, price  from printer where price = (select max(price) from printer)
```

## 11
https://sql-ex.ru/learn_exercises.php?LN=11
Найдите среднюю скорость ПК.
select avg (speed) from pc

## 12
https://sql-ex.ru/learn_exercises.php?LN=12

```
Select avg(speed) from laptop where price > 1000
```

## 13
https://sql-ex.ru/learn_exercises.php?LN=13

```
Select avg(speed) from pc inner join product on pc.model= product.model where maker = 'A'   
group by maker 
```

## 14
https://sql-ex.ru/learn_exercises.php?LN=14

```
    Select s.class, s.name, c.country from classes c join ships s on c.class = s.class where numguns >= '10';
```

## 15
https://sql-ex.ru/learn_exercises.php?LN=15

```
Select hd  from pc group by hd having count(model)>1
```

## 16
https://sql-ex.ru/learn_exercises.php?LN=16

```
SELECT DISTINCT B.model AS model, A.model AS model, A.speed, A.ram 
FROM PC AS A, PC B 
WHERE A.speed = B.speed AND A.ram = B.ram and A.model < B.model 
```

## 17
https://sql-ex.ru/learn_exercises.php?LN=17

```
Select distinct type,laptop.model,speed from laptop inner join product on laptop.model= product.model  
where speed < (select MIN(speed) from pc) 
```

## 18
https://sql-ex.ru/learn_exercises.php?LN=18

```
SELECT DISTINCT maker,price  FROM printer inner JOIN product ON printer.model= product.model  
WHERE price = (select min(price)from printer where color = 'y' ) and color = 'y' 
```

## 19
https://sql-ex.ru/learn_exercises.php?LN=19

```
Select maker, avg(screen)as Avg_screen 
from laptop inner join product on laptop.model =  product.model group by maker 
```

## 20
https://sql-ex.ru/learn_exercises.php?LN=20

```
Select maker , count(model) as Count_Model from product where type = 'pc' group by maker 
having count(model) >= 3
```

## 21
https://sql-ex.ru/learn_exercises.php?LN=21

```
Select maker , max(price)as Max_price from pc inner join product on pc.model= product.model  
group by maker
```
    
## 22
https://sql-ex.ru/learn_exercises.php?LN=22

```
Select speed , avg(price) as Avg_price from pc  where speed > 600 group by speed
```
    
## 23
https://sql-ex.ru/learn_exercises.php?LN=23
Найдите производителей, которые производили бы как ПКсо скоростью не менее 750 МГц, так и ПК-блокноты со скоростью не менее 750 МГц.Вывести: Maker
select distinct maker  from pc inner join product on pc.model = product.model  
where pc.speed >= 750 and maker in (select  maker  
from laptop inner join product on laptop.model = product.model where laptop.speed >= 750) 

    
## 24
https://sql-ex.ru/learn_exercises.php?LN=24

```
SELECT model FROM( 
SELECT distinct model, price FROM laptop WHERE laptop.price = (SELECT MAX(price) FROM laptop)  
UNION 
SELECT distinct model, price FROM pc WHERE pc.price = (SELECT MAX(price) FROM pc)  
UNION 
SELECT distinct model, price FROM printer WHERE printer.price = (SELECT MAX(price) FROM printer)  
) as t 
WHERE t.price=(SELECT MAX(price) FROM ( 
SELECT distinct price FROM laptop WHERE laptop.price = (SELECT MAX(price) FROM laptop)  
UNION 
SELECT distinct price FROM pc WHERE pc.price = (SELECT MAX(price) FROM pc)  
UNION 
SELECT distinct price FROM printer WHERE printer.price = (SELECT MAX(price) FROM printer)  
) as t1 )
```

## 25
https://sql-ex.ru/learn_exercises.php?LN=25

```
SELECT distinct product.maker FROM product WHERE product.type='Printer'  
INTERSECT 
SELECT distinct product.maker FROM product INNER JOIN pc ON pc.model=product.model  
WHERE product.type='PC' AND pc.ram=(SELECT MIN(ram) FROM pc)  
AND pc.speed = (SELECT MAX(speed) FROM (SELECT distinct speed FROM pc 
WHERE pc.ram=(SELECT MIN(ram) FROM pc)) as t)
```

## 26
https://sql-ex.ru/learn_exercises.php?LN=26

```
SELECT t1.c/t1.d FROM( SELECT SUM(t.a) as c, SUM(t.b) as d FROM(  
SELECT SUM(pc.price) as a, COUNT(pc.code) as b FROM pc 
INNER JOIN product ON pc.model=product.model WHERE product.maker='A'  
UNION 
SELECT SUM(laptop.price) as a, COUNT(laptop.code) as b FROM laptop 
INNER JOIN product ON laptop.model=product.model WHERE product.maker='A') as t) as t1
```
    
## 27
https://sql-ex.ru/learn_exercises.php?LN=27

```
select maker,avg(hd)  from product inner join pc on product.model=pc.model   
where maker in(select maker  from product  where type='printer')  group by maker 
```
    
## 28
https://sql-ex.ru/learn_exercises.php?LN=28

    
## 29
https://sql-ex.ru/learn_exercises.php?LN=29

```
select t.point, t.date, SUM(t.inc), sum(t.out) from( select point, date, inc, null as out from Income_o  
Union 
select point, date, null as inc, Outcome_o.out from Outcome_o) as t group by t.point, t.date 
```

## 30
https://sql-ex.ru/learn_exercises.php?LN=30

```
select point, date, SUM(sum_out), SUM(sum_inc) 
from( select point, date, SUM(inc) as sum_inc, null as sum_out from Income Group by point, date  
Union 
select point, date, null as sum_inc, SUM(out) as sum_out from Outcome Group by point, date ) as t  
group by point, date order by point
```

## 31
https://sql-ex.ru/learn_exercises.php?LN=31

```
Select class , country from classes where bore >= 16 
```

## 32
https://sql-ex.ru/learn_exercises.php?LN=32

```
Select country, cast(avg((power(bore,3)/2)) as numeric(6,2)) as weight 
from (select country, classes.class, bore, name from classes left join ships on classes.class=ships.class  
union all 
select distinct country, class, bore, ship from classes t1 left join outcomes t2 on t1.class=t2.ship  
where ship=class and ship not in (select name from ships) ) a  
where name!='null' group by country
```
## 33
https://sql-ex.ru/learn_exercises.php?LN=33

```
Select ship from outcomes,battles where result= 'sunk' and battle = 'North Atlantic' group by ship  
```
## 34
https://sql-ex.ru/learn_exercises.php?LN=34

```
Select name from classes,ships where launched >=1922 and displacement>35000 and type='bb' and
ships.class = classes.class
```
## 35
https://sql-ex.ru/learn_exercises.php?LN=35

```
SELECT model, type FROM product 
WHERE model NOT LIKE '%[^0-9]%' OR model NOT LIKE '%[^a-z]%'
```
## 36
https://sql-ex.ru/learn_exercises.php?LN=36

```
Select name  from ships  where class = name   
union  
select ship as name  from classes,outcomes  where classes.class = outcomes.ship  
```
## 37
https://sql-ex.ru/learn_exercises.php?LN=37

```
Select 
	c.class 
From Classes c
Left Join (Select class, name 
	From Ships
	Union
Select 
	Classes.class as class, Outcomes.ship as name
From Outcomes
Join Classes ON Outcomes.ship = Classes.class) as s On c.class = s.class
Group by c.class
Having count(s.name)=1
```
## 38
https://sql-ex.ru/learn_exercises.php?LN=38

```
Select distinct country  from classes  where type='bb'   
intersect  
Select distinct country  from classes  where type='bc'  
```
## 39
https://sql-ex.ru/learn_exercises.php?LN=39

```
select distinct ccc.sh from ( select aaa.ship as sh, aaa.[date] as d1, bbb.[date] as d2 from ( 
select ship, [date] from outcomes as o inner join battles as b on o.battle=b.name where result = 'damaged') as aaa inner join (select ship,  
[date] from outcomes as o inner join battles as b on o.battle=b.name) as bbb on aaa.ship=bbb.ship 
where bbb.date > aaa.date) as ccc
```
## 40
https://sql-ex.ru/learn_exercises.php?LN=40

```
select maker, type from product
where maker in (SELECT maker FROM
(SELECT maker, type FROM Product GROUP BY maker, type) Alias
group by maker having count(maker) = 1) group by maker, type having count(type)>1
```
## 41
https://sql-ex.ru/learn_exercises.php?LN=41

```
with D as
(select model, price from PC
union
select model, price from Laptop
union
select model, price from Printer)
Select distinct P.maker,
CASE WHEN MAX(CASE WHEN D.price IS NULL THEN 1 ELSE 0 END) = 0 THEN
MAX(D.price) END
from Product P
right join D on P.model=D.model
group by P.maker
```
## 42
https://sql-ex.ru/learn_exercises.php?LN=42

```
Select 
	ship, battle
From Outcomes
Where result = 'sunk'
```

## 43
https://sql-ex.ru/learn_exercises.php?LN=43

```
select name from battles where DATEPART(yy, date) not in (select DATEPART(yy, date)  
from battles join ships on DATEPART(yy, date)=launched) 
```
## 44
https://sql-ex.ru/learn_exercises.php?LN=44

```
Select name from ships where name like 'R%'   
union   
Select name from battles where name like 'R%'   
union   
Select ship from outcomes where ship like 'R%'
```
## 45
https://sql-ex.ru/learn_exercises.php?LN=45

```
Select name from ships where name like '% % %'  
union   
Select ship from outcomes where ship like '% % %'  
```
## 46
https://sql-ex.ru/learn_exercises.php?LN=46
```
select name as n, displacement as d, numguns as ng from ships inner join classes on ships.class=classes.class where name in (select ship from outcomes where battle = 'Guadalcanal')   
union 
select ship as n, displacement as d, numguns as ng from outcomes inner join classes on outcomes.ship=classes.class where battle = 'Guadalcanal' and ship not in (select name from ships)   
union  
select ship as n, null as d, null as ng from outcomes where battle = 'Guadalcanal' and ship not in (select name from ships) and ship not in  (select class from classes)   
```

## 47
https://sql-ex.ru/learn_exercises.php?LN=47

```
    WITH out AS (SELECT *
FROM outcomes JOIN (SELECT ships.name s_name, classes.class s_class, classes.country s_country
FROM ships FULL JOIN classes
ON ships.class = classes.class
) u
ON outcomes.ship=u.s_class
UNION
SELECT *
FROM outcomes JOIN (SELECT ships.name s_name, classes.class s_class, classes.country s_country
FROM ships FULL JOIN classes
ON ships.class = classes.class
) u
ON outcomes.ship=u.s_name)
SELECT fin.country
FROM (
SELECT DISTINCT t.country, COUNT(t.name) AS num_ships
FROM (
select distinct c.country, s.name
from classes c
inner join Ships s on s.class= c.class
union
select distinct c.country, o.ship
from classes c
inner join Outcomes o on o.ship= c.class) t
GROUP BY t.country


INTERSECT


SELECT out.s_country, COUNT(out.ship) AS num_ships
FROM out
WHERE out.result='sunk'
GROUP BY out.s_country) fin;
```

## 48
https://sql-ex.ru/learn_exercises.php?LN=48

```Select class as n from ships where name in(select ship from outcomes where result='sunk')   
union  
Select ship as n from outcomes  
where ship not in(Select name from ships) and ship in(Select class from classes) and result='sunk'  
```

## 49
https://sql-ex.ru/learn_exercises.php?LN=49

```
select name from ships where class in( Select class from classes where bore=16)   
union  
select ship from outcomes where ship in( Select class from classes where bore=16)  
```

## 50
https://sql-ex.ru/learn_exercises.php?LN=50
```
SELECT distinct battle FROM Classes  inner JOIN Ships  ON ships.class = classes.class   
inner JOIN Outcomes  ON Classes.class=Outcomes.ship or Ships.name=Outcomes.ship   
WHERE classes.class = 'Kongo'  
```

## 51
https://sql-ex.ru/learn_exercises.php?LN=51
```
select NAME from(select name as NAME, displacement, numguns  
from ships inner join classes on ships.class = classes.class 
union 
select ship as NAME, displacement, numguns from outcomes inner join classes on outcomes.ship= classes.class) as d1 inner join (select displacement, max(numGuns) as numguns from ( select displacement, numguns from ships inner join classes on ships.class = classes.class  
union 
select displacement, numguns  from outcomes inner join classes on outcomes.ship= classes.class) as f 
group by displacement) as d2 on d1.displacement=d2.displacement and d1.numguns =d2.numguns 
```

## 52
https://sql-ex.ru/learn_exercises.php?LN=52
```
Select distinct name from ships  inner join classes cl on ships.class=cl.class 
where (numGuns>=9 or numguns is NULL) and (bore<19 or bore is NULL) and (displacement<=65000 or displacement is NULL) and type='bb' and country='japan' 
```


## 53
https://sql-ex.ru/learn_exercises.php?LN=53
```
select cast(avg(numguns*1.0) as numeric(4,2)) as Avg_numGuns  from classes where type='bb' 
```

## 54
https://sql-ex.ru/learn_exercises.php?LN=54
```
SELECT CAST(AVG(numguns*1.0) AS NUMERIC (4,2)) as AVG_nmg 
FROM (SELECT ship, type, numguns   FROM Outcomes LEFT JOIN Classes ON ship = class  
UNION  
SELECT name, type, numguns FROM Ships as S INNER JOIN  Classes as C ON c.class = s.class ) AS T 
WHERE type = 'bb' 
```

## 55
https://sql-ex.ru/learn_exercises.php?LN=55
```
select C.class, min(launched)  from ships as S right join classes as C on s.class=c.class group by C.class 
```

## 56
https://sql-ex.ru/learn_exercises.php?LN=56
```
    SELECT c.class, COUNT(s.ship)
FROM classes c
LEFT JOIN (SELECT o.ship, sh.class
FROM outcomes o
LEFT JOIN ships sh ON sh.name = o.ship
WHERE o.result = 'sunk') AS s ON s.class = c.class OR s.ship = c.class
GROUP BY c.class;
```

## 57
https://sql-ex.ru/learn_exercises.php?LN=57
```
select class as cls, count(class) as sunked from( 
select C.class, O.ship from classes as C join outcomes as O on C.class=O.ship where O.result='sunk' 
union 
select S.class, O.ship from outcomes as O join ships as S on S.name=O.ship where O.result='sunk') as T 
where class in ( select distinct X.class from  (select C.class, O.ship from classes as C join outcomes as O on C.class=O.ship 
union 
select C.class, S.name from classes as C join ships as S on C.class=S.class) as X group by X.class 
having count(X.class)>=3 )  group by class 
```

## 58
https://sql-ex.ru/learn_exercises.php?LN=58
```
select main_maker ,main_type ,CONVERT(NUMERIC(6,2),((sub_num*100.00)/(total_num*100.00)*100.00))  
from (select count(p5.model) total_num ,p5.maker main_maker 
 from product p5 group by p5.maker) p6 JOIN (select p3.maker sub_maker ,p3.type main_type ,count(p4.model) sub_num 
 from (select p1.maker maker, p2.type type from product p1 cross join product p2 group by p1.maker, p2.type) p3 left join product p4 on p3.maker = p4.maker and p3.type = p4.type group by  p3.maker,p3.type) p7 ON p7.sub_maker = p6.main_maker 
```

## 59
https://sql-ex.ru/learn_exercises.php?LN=59
```
select a.point, case when o is null then i else i-o end remain FROM  (select point, sum(inc) as i 
from Income_o group by point) as A left join (select point, sum(out) as o from Outcome_o group by point) as B on A.point=B.point 
```

## 60
https://sql-ex.ru/learn_exercises.php?LN=60
```
select a.point,  case when o is null  then i else i-o end remain FROM (select point, sum(inc) as i 
from Income_o where '20010415' > date group by point) as A left join (select point, sum(out) as o 
from Outcome_o  where '20010415' > date group by point) as B on A.point=B.point  
```

## 61
https://sql-ex.ru/learn_exercises.php?LN=61
```
select (select sum(inc) from income_o) - (select sum(out) from outcome_o) as remain  
```

## 62
https://sql-ex.ru/learn_exercises.php?LN=62
```
select  (select sum(inc) from income_o where '20010415' > date)   
-  
(select sum(out) from outcome_o where '20010415' > date)  as remain 
```

## 63
https://sql-ex.ru/learn_exercises.php?LN=63
```
select name from Passenger where ID_psg in(Select Left([ol],CHARINDEX ( ' ', ol)) from ( 
Select CAST(concat(ID_psg,' ', place) AS VARCHAR(30)) as ol, trip_no as o, ID_psg as psg 
from Pass_in_trip ) as lll group by ol having count(o)>1) 
```

## 64
https://sql-ex.ru/learn_exercises.php?LN=64
```
Select income.point, income.date, 'inc' as operation, sum(income.inc) 
from income left join outcome on income.point=outcome.point and income.date=outcome.date 
where outcome.date is null  group by income.point, income.date 
union 
Select outcome.point, outcome.date, 'out' as operation, sum(outcome.out) 
from income right join outcome on income.point=outcome.point and income.date=outcome.date 
where income.date is null group by outcome.point, outcome.date 
```

## 65
https://sql-ex.ru/learn_exercises.php?LN=65
```
    SELECT row_number() over(ORDER BY maker,s),t, type FROM
(SELECT maker,type,
CASE
WHEN type='PC'
THEN 0
WHEN type='Laptop'
THEN 1
ELSE 2
END AS s,
CASE
WHEN type='Laptop' AND (maker in (SELECT maker FROM Product WHERE
type='PC'))
THEN 
WHEN type='Printer' AND ((maker in (SELECT maker FROM Product WHERE
type='PC')) OR (maker in (SELECT maker FROM Product WHERE
type='Laptop')))
THEN ''
ELSE maker
END AS t
FROM Product
GROUP BY maker,type) AS t1
ORDER BY maker, s;
```

## 66
https://sql-ex.ru/learn_exercises.php?LN=66
```
    SELECT date, max(c) FROM
(SELECT date,count(*) AS c FROM Trip,
(SELECT trip_no,date FROM Pass_in_trip WHERE date>='2003-04-01' AND date<='2003-04-07' GROUP BY trip_no, date) AS t1
WHERE Trip.trip_no=t1.trip_no AND town_from='Rostov'
GROUP BY date
UNION ALL
SELECT '2003-04-01',0
UNION ALL
SELECT '2003-04-02',0
UNION ALL
SELECT '2003-04-03',0
UNION ALL
SELECT '2003-04-04',0
UNION ALL
SELECT '2003-04-05',0
UNION ALL
SELECT '2003-04-06',0
UNION ALL
SELECT '2003-04-07',0) AS t2
GROUP BY date;
```

## 67
https://sql-ex.ru/learn_exercises.php?LN=67
```
select count(qqq) as qty from ( select town_from as qqq, town_to, count(plane) as cp from Trip 
group by town_from, town_to having count(plane) >= all(select count(plane)  from Trip 
group by town_from, town_to) ) as tab 
```

## 68
https://sql-ex.ru/learn_exercises.php?LN=68
```
    select count(*) from (
select TOP 1 WITH TIES sum(c) cc, c1, c2 from (
SELECT count(*) c, town_from c1, town_to c2 from trip
where town_from>=town_to
group by town_from, town_to
union all
SELECT count(*) c,town_to, town_from from trip
where town_to>town_from
group by town_from, town_to
) as t
group by c1,c2
order by cc desc
) as tt;
```

## 69
https://sql-ex.ru/learn_exercises.php?LN=69
```
    select
  row_number() over(order by maker) as num
  ,CASE WHEN mnum=1 THEN maker
    ELSE ''
  END as maker
  ,type
  from (
    select
    row_number() over(partition by maker order by maker, ord) as mnum
    ,maker
    ,type
    from (
    select
      distinct maker, type
      ,CASE WHEN LOWER(type)='pc' then 1
            WHEN LOWER(type)='laptop' then 2
            ELSE 3
      END as ord
      from product
    ) as mto
  ) as mtn;
```

## 70
https://sql-ex.ru/learn_exercises.php?LN=70
```
    SELECT DISTINCT o.battle
FROM outcomes o
LEFT JOIN ships s ON s.name = o.ship
LEFT JOIN classes c ON o.ship = c.class OR s.class = c.class
WHERE c.country IS NOT NULL
GROUP BY c.country, o.battle
HAVING COUNT(o.ship) >= 3;
```

## 71
https://sql-ex.ru/learn_exercises.php?LN=71
```
select p.maker from product p where p.type='pc' group by p.maker having count(DISTINCT p.model) = ( select count(DISTINCT pc.model) from pc where pc.model in ( select DISTINCT pr.model from product pr where pr.maker=p.maker )) 
```

## 72
https://sql-ex.ru/learn_exercises.php?LN=72
```
    select TOP 1 WITH TIES name, c3 from passenger
join
(select c1, max(c3) c3 from
(
select pass_in_trip.ID_psg c1, Trip.ID_comp c2, count(*) c3 from pass_in_trip
join trip on trip.trip_no=pass_in_trip.trip_no
group by pass_in_trip.ID_psg, Trip.ID_comp
) as t
group by c1
having count(*)=1) as tt
on ID_psg=c1
order by c3 desc;
```

## 73
https://sql-ex.ru/learn_exercises.php?LN=73
```
    SELECT DISTINCT c.country, b.name
FROM battles b, classes c
MINUS
SELECT c.country, o.battle
FROM outcomes o
LEFT JOIN ships s ON s.name = o.ship
LEFT JOIN classes c ON o.ship = c.class OR s.class = c.class
WHERE c.country IS NOT NULL
GROUP BY c.country, o.battle;
```

## 74
https://sql-ex.ru/learn_exercises.php?LN=74
```
select c.country, c.class from classes c where c.country like (case when  (select count(*) from classes c 
where c.country='Russia' group by c.country) is not null THEN ('Russia') else ('%') end) 
```

## 75
https://sql-ex.ru/learn_exercises.php?LN=75
```
    select shipname,launched,batname
from
(select s.name as shipname,launched,b.name as batname,
row_number() over (partition by s.name order by "date") as num
from ships s,battles b
where to_char("date",'yyyy')>=launched
and launched is not null)
where num = 1
union
(
select name,launched,(select name from battles
where "date" = (select max("date") from battles)) as batname
from ships
where launched is null
);
```

## 76
https://sql-ex.ru/learn_exercises.php?LN=76
```

```

## 77
https://sql-ex.ru/learn_exercises.php?LN=77
```

    SELECT TOP 1 WITH TIES * FROM (
  SELECT COUNT (DISTINCT P.trip_no) count, date
  FROM Pass_in_trip P
  JOIN Trip T ON T.trip_no = P.trip_no AND town_from = 'Rostov'
  GROUP BY P.trip_no, date) X
ORDER BY 1 DESC;
```


## 78
https://sql-ex.ru/learn_exercises.php?LN=78
```
    SELECT name, REPLACE(CONVERT(CHAR(12), DATEADD(m, DATEDIFF(m,0,date),0), 102),'.','-') AS first_day,
             REPLACE(CONVERT(CHAR(12), DATEADD(s,-1,DATEADD(m, DATEDIFF(m,0,date)+1,0)), 102),'.','-') AS last_day
FROM Battles;
```


## 79
https://sql-ex.ru/learn_exercises.php?LN=79
```
    SELECT Passenger.name, A.minutes
FROM (SELECT P.ID_psg,
      SUM((DATEDIFF(minute, time_out, time_in) + 1440)%1440) AS minutes,
      MAX(SUM((DATEDIFF(minute, time_out, time_in) + 1440)%1440)) OVER() AS MaxMinutes
      FROM Pass_in_trip P JOIN
       Trip AS T ON P.trip_no = T.trip_no
      GROUP BY P.ID_psg
      ) AS A JOIN
 Passenger ON Passenger.ID_psg = A.ID_psg
WHERE A.minutes = A.MaxMinutes;
```



## 80
https://sql-ex.ru/learn_exercises.php?LN=80
```
select distinct maker from product  where maker not in ( select maker from product  where model in ( 
select model from product where type='pc' except select model from pc ) ) 
```


## 81
https://sql-ex.ru/learn_exercises.php?LN=81
```
    SELECT O.*
FROM outcome O
INNER JOIN
(
SELECT TOP 1 WITH TIES YEAR(date) AS Y, MONTH(date) AS M, SUM(out) AS ALL_TOTAL
FROM outcome
GROUP BY YEAR(date), MONTH(date)
ORDER BY ALL_TOTAL DESC
) R ON YEAR(O.date) = R.Y AND MONTH(O.date) = R.M;
```


## 82
https://sql-ex.ru/learn_exercises.php?LN=82
```
    WITH CTE(code,price,number)
AS
(
SELECT PC.code,PC.price, number= ROW_NUMBER() OVER (ORDER BY PC.code)
FROM PC
)
SELECT CTE.code, AVG(C.price)
FROM CTE
JOIN CTE C ON (C.number-CTE.number)<6 AND (C.number-CTE.number)> =0
GROUP BY CTE.number,CTE.code
HAVING COUNT(CTE.number)=6;
```


## 83
https://sql-ex.ru/learn_exercises.php?LN=83
```
    SELECT name
FROM Ships AS s JOIN Classes AS cl1 ON s.class = cl1.class
WHERE
CASE WHEN numGuns = 8 THEN 1 ELSE 0 END +
CASE WHEN bore = 15 THEN 1 ELSE 0 END +
CASE WHEN displacement = 32000 THEN 1 ELSE 0 END +
CASE WHEN type = 'bb' THEN 1 ELSE 0 END +
CASE WHEN launched = 1915 THEN 1 ELSE 0 END +
CASE WHEN s.class = 'Kongo' THEN 1 ELSE 0 END +
CASE WHEN country = 'USA' THEN 1 ELSE 0 END > = 4;
```


## 84
https://sql-ex.ru/learn_exercises.php?LN=84
```
    SELECT C.name, A.N_1_10, A.N_11_21, A.N_21_30
FROM (SELECT T.ID_comp,
       SUM(CASE WHEN DAY(P.date) < 11 THEN 1 ELSE 0 END) AS N_1_10,
       SUM(CASE WHEN (DAY(P.date) > 10 AND DAY(P.date) < 21) THEN 1 ELSE 0 END) AS N_11_21,
       SUM(CASE WHEN DAY(P.date) > 20 THEN 1 ELSE 0 END) AS N_21_30
      FROM Trip AS T JOIN
       Pass_in_trip AS P ON T.trip_no = P.trip_no AND CONVERT(char(6), P.date, 112) = '200304'
      GROUP BY T.ID_comp
      ) AS A JOIN
 Company AS C ON A.ID_comp = C.ID_comp;
```

## 85
https://sql-ex.ru/learn_exercises.php?LN=85
```
select maker from ( select maker from product where type='printer'  except  
select maker from product where type='laptop' except select maker from product where type='pc' ) as T 
union 
select maker from ( select maker from product inner join pc on pc.model=product.model group by maker 
having count(maker)>=3 except select maker from product where type='laptop' except  
select maker from product where type='printer' ) as S 
```


## 86
https://sql-ex.ru/learn_exercises.php?LN=86
```
    SELECT maker,
       CASE count(distinct type) when 2 then MIN(type) + '/' + MAX(type)
                                 when 1 then MAX(type)
                                 when 3 then 'Laptop/PC/Printer' END
FROM Product
GROUP BY maker;
```


## 87
https://sql-ex.ru/learn_exercises.php?LN=87
```
    SELECT DISTINCT name, COUNT(town_to) Qty
FROM Trip tr JOIN Pass_in_trip pit ON tr.trip_no = pit.trip_no JOIN
         Passenger psg ON pit.ID_psg = psg.ID_psg
WHERE town_to = 'Moscow' AND pit.ID_psg NOT IN(SELECT DISTINCT ID_psg
FROM Trip tr JOIN Pass_in_trip pit ON tr.trip_no = pit.trip_no
WHERE date+time_out = (SELECT MIN (date+time_out)
                       FROM Trip tr1 JOIN Pass_in_trip pit1 ON tr1.trip_no = pit1.trip_no
                       WHERE pit.ID_psg = pit1.ID_psg)
AND town_from = 'Moscow')
GROUP BY pit.ID_psg, name
HAVING COUNT(town_to) > 1;
```


## 88
https://sql-ex.ru/learn_exercises.php?LN=88
```
    SELECT
 (SELECT name FROM Passenger WHERE ID_psg = B.ID_psg) AS name,
 B.trip_Qty,
 (SELECT name FROM Company WHERE ID_comp = B.ID_comp) AS Company
FROM (SELECT P.ID_psg, MIN(T.ID_comp) AS ID_comp, COUNT(*) AS trip_Qty, MAX(COUNT(*)) OVER() AS Max_Qty
      FROM Pass_in_trip AS P JOIN
       Trip AS T ON P.trip_no = T.trip_no
      GROUP BY P.ID_psg
      HAVING MIN(T.ID_comp) = MAX(T.ID_comp)
      ) AS B
WHERE B.trip_Qty = B.Max_Qty;
```


## 89
https://sql-ex.ru/learn_exercises.php?LN=89
```
select maker, count(maker) from product group by maker  having count(maker) in (  
select max(D.cnt) from  ( select maker, count(maker) as cnt from product group by maker ) as D 
union 
select min(F.cnt) from ( select maker, count(maker) as cnt from product group by maker ) as F ) 
```


## 90
https://sql-ex.ru/learn_exercises.php?LN=90
```
    Select maker, model, type from
(
Select
row_number() over (order by model) p1,
row_number() over (order by model DESC) p2,
from Product
) t1
where p1 > 3 and p2 > 3;
```

## 91
https://sql-ex.ru/learn_exercises.php?LN=91
```
select count(*)  from ( select maker from product group by maker having count(model)=1 ) as Q
```


## 92
https://sql-ex.ru/learn_exercises.php?LN=92
```

    SELECT Q_NAME
FROM utQ
WHERE Q_ID IN (SELECT DISTINCT B.B_Q_ID
                FROM (SELECT B_Q_ID
                        FROM utB
                        GROUP BY B_Q_ID
                        HAVING SUM(B_VOL) = 765) AS B
                WHERE B.B_Q_ID NOT IN (SELECT B_Q_ID
                                        FROM utB
                                        WHERE B_V_ID IN (SELECT B_V_ID
                                                          FROM utB
                                                          GROUP BY B_V_ID
                                                          HAVING SUM(B_VOL) < 255)));
```


## 93
https://sql-ex.ru/learn_exercises.php?LN=93
```
    select c.name, sum(vr.vr)
from
(select distinct t.id_comp, pt.trip_no, pt.date,t.time_out,t.time_in,--pt.id_psg,
case
     when DATEDIFF(mi, t.time_out,t.time_in)> 0 then DATEDIFF(mi, t.time_out,t.time_in)
     when DATEDIFF(mi, t.time_out,t.time_in)<=0 then DATEDIFF(mi, t.time_out,t.time_in+1)
end vr
from pass_in_trip pt left join trip t on pt.trip_no=t.trip_no
) vr left join company c on vr.id_comp=c.id_comp
group by c.name;
```


## 94
https://sql-ex.ru/learn_exercises.php?LN=94
```
   SELECT DATEADD(day, S.Num, D.date) AS Dt,
       (SELECT COUNT(DISTINCT P.trip_no)
        FROM Pass_in_trip P
               JOIN Trip T
                 ON P.trip_no = T.trip_no
                    AND T.town_from = 'Rostov'
                    AND P.date = DATEADD(day, S.Num, D.date)) AS Qty
FROM (SELECT (3 * ( x - 1 ) + y - 1) AS Num
        FROM (SELECT 1 AS x UNION ALL SELECT 2 UNION ALL SELECT 3) AS N1
               CROSS JOIN (SELECT 1 AS y UNION ALL SELECT 2 UNION ALL SELECT 3) AS N2
        WHERE (3 * ( x - 1 ) + y ) < 8) AS S,
       (SELECT MIN(A.date) AS date
        FROM (SELECT P.date,
                       COUNT(DISTINCT P.trip_no) AS Qty,
                       MAX(COUNT(DISTINCT P.trip_no)) OVER() AS M_Qty
                FROM Pass_in_trip AS P
                       JOIN Trip AS T
                         ON P.trip_no = T.trip_no
                            AND T.town_from = 'Rostov'
                GROUP BY P.date) AS A
        WHERE A.Qty = A.M_Qty) AS D;
```



## 95
https://sql-ex.ru/learn_exercises.php?LN=95
```
    SELECT name,
    COUNT(DISTINCT CONVERT(CHAR(24),date)+CONVERT(CHAR(4),Trip.trip_no)),
    COUNT(DISTINCT plane),
    COUNT(DISTINCT ID_psg),
    COUNT(*)
FROM Company,Pass_in_trip,Trip
WHERE Company.ID_comp=Trip.ID_comp and Trip.trip_no=Pass_in_trip.trip_no
GROUP BY Company.ID_comp,name;
```



## 96
https://sql-ex.ru/learn_exercises.php?LN=96
```
    with r as (select v.v_name,
       v.v_id,
       count(case when v_color = 'R' then 1 end) over(partition by v_id) cnt_r,
       count(case when v_color = 'B' then 1 end) over(partition by b_q_id) cnt_b
  from utV v join utB b on v.v_id = b.b_v_id)
select v_name
  from r
where cnt_r > 1
  and cnt_b > 0
group by v_name;
```



## 97
https://sql-ex.ru/learn_exercises.php?LN=97
```
    select code, speed, ram, price, screen
from laptop where exists (
  select 1 x
  from (
    select v, rank()over(order by v) rn
    from ( select cast(speed as float) sp, cast(ram as float) rm,
                  cast(price as float) pr, cast(screen as float) sc
    )l unpivot(v for c in (sp, rm, pr, sc))u
  )l pivot(max(v) for rn in ([1],[2],[3],[4]))p
  where [1]*2 <= [2] and [2]*2 <= [3] and [3]*2 <= [4]
);
```


## 98
https://sql-ex.ru/learn_exercises.php?LN=98
```
with CTE AS
(select
1 n, cast (0 as varchar(16)) bit_or,
code, speed, ram FROM PC
UNION ALL
select n*2,
cast (convert(bit,(speed|ram)&n) as varchar(1))+cast(bit_or as varchar(15))
, code, speed, ram
from CTE where n < 65536
)
select code, speed, ram from CTE
where n = 65536
and CHARINDEX('1111', bit_or )> 0;
```


## 99
https://sql-ex.ru/learn_exercises.php?LN=99
```
    select point,
       "date" income_date,
       "date" + nvl(
                  min(case when diff > cnt then cnt else null end),
                  max(cnt)+1
                ) incass_date
from (select i.point,
             i."date",
             (trunc(o."date") - trunc(i."date")) diff, -- разница дней
             -- количество запрещенных для инкассации дней после прихода и до текущего запрещенного дня
             count(1) over (partition by i.point, i."date" order by o."date" rows between unbounded preceding and current row)-1 cnt
      from income_o i
               join (select point, "date", 1 disabled from outcome_o
                     union
                     select point, trunc("date"+7,'DAY'), 1 disabled from income_o) o
                 on i.point = o.point
      where o."date" > = i."date")
group by point, "date";
```


## 100
https://sql-ex.ru/learn_exercises.php?LN=100
```
    Select distinct A.date , A.R, B.point, B.inc, C.point, C.out
From (Select distinct date, ROW_Number() OVER(PARTITION BY date ORDER BY code asc) as R From Income
Union Select distinct date, ROW_Number() OVER(PARTITION BY date ORDER BY code asc) From Outcome) A
LEFT Join (Select date, point, inc
                , ROW_Number() OVER(PARTITION BY date ORDER BY code asc) as RI FROM Income
           ) B on B.date=A.date and B.RI=A.R
LEFT Join (Select date, point, out
                , ROW_Number() OVER(PARTITION BY date ORDER BY code asc) as RO FROM Outcome
           ) C on C.date=A.date and C.RO=A.R;
```

