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

18
https://sql-ex.ru/learn_exercises.php?LN=18

19
https://sql-ex.ru/learn_exercises.php?LN=19

20
https://sql-ex.ru/learn_exercises.php?LN=20
