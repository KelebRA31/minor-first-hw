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

```

## 66
https://sql-ex.ru/learn_exercises.php?LN=66
```

```

## 67
https://sql-ex.ru/learn_exercises.php?LN=67
```

```

## 68
https://sql-ex.ru/learn_exercises.php?LN=68
```

```

## 69
https://sql-ex.ru/learn_exercises.php?LN=69
```

```

## 70
https://sql-ex.ru/learn_exercises.php?LN=70
```

```

## 71
https://sql-ex.ru/learn_exercises.php?LN=71
```

```

## 72
https://sql-ex.ru/learn_exercises.php?LN=72
```

```

## 73
https://sql-ex.ru/learn_exercises.php?LN=73
```

```

## 74
https://sql-ex.ru/learn_exercises.php?LN=74
```

```

## 75
https://sql-ex.ru/learn_exercises.php?LN=75
```

```

## 76
https://sql-ex.ru/learn_exercises.php?LN=76
```

```

## 77
https://sql-ex.ru/learn_exercises.php?LN=77


## 78
https://sql-ex.ru/learn_exercises.php?LN=78


## 79
https://sql-ex.ru/learn_exercises.php?LN=79


## 80
https://sql-ex.ru/learn_exercises.php?LN=80


## 81
https://sql-ex.ru/learn_exercises.php?LN=81


## 82
https://sql-ex.ru/learn_exercises.php?LN=82


## 83
https://sql-ex.ru/learn_exercises.php?LN=83


## 84
https://sql-ex.ru/learn_exercises.php?LN=84

## 85
https://sql-ex.ru/learn_exercises.php?LN=85


## 86
https://sql-ex.ru/learn_exercises.php?LN=86


## 87
https://sql-ex.ru/learn_exercises.php?LN=87


## 88
https://sql-ex.ru/learn_exercises.php?LN=88


## 89
https://sql-ex.ru/learn_exercises.php?LN=89


## 90
https://sql-ex.ru/learn_exercises.php?LN=90


## 91
https://sql-ex.ru/learn_exercises.php?LN=91


## 92
https://sql-ex.ru/learn_exercises.php?LN=92


## 93
https://sql-ex.ru/learn_exercises.php?LN=93


## 94
https://sql-ex.ru/learn_exercises.php?LN=94



## 95
https://sql-ex.ru/learn_exercises.php?LN=95



## 96
https://sql-ex.ru/learn_exercises.php?LN=96



## 97
https://sql-ex.ru/learn_exercises.php?LN=97


## 98
https://sql-ex.ru/learn_exercises.php?LN=98


## 99
https://sql-ex.ru/learn_exercises.php?LN=99


## 100
https://sql-ex.ru/learn_exercises.php?LN=100

