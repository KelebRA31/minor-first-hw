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
