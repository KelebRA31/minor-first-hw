# minor-first-hw


##1
https://sql-ex.ru/learn_exercises.php?LN=1

```SELECT model, speed, hd FROM PC WHERE price < 500```

2
https://sql-ex.ru/learn_exercises.php?LN=2
Найдите производителей принтеров. Вывести: maker
Select maker  from  product where product.type = 'printer' group by maker

3
https://sql-ex.ru/learn_exercises.php?LN=3
Найдите все записи таблицы Printer для цветных принтеров.
select * from printer where color = 'y'

4
https://sql-ex.ru/learn_exercises.php?LN=4
Найдите все записи таблицы Printer для цветных принтеров.
select * from printer where color = 'y'

5
https://sql-ex.ru/learn_exercises.php?LN=5
Найдите номер модели, скорость и размер жесткого диска ПК, имеющих 12x или 24x CD и цену менее 600 дол.
Select model ,speed , hd  from pc where (cd = '12x' or cd = '24x') and price < 600

6!
https://sql-ex.ru/learn_exercises.php?LN=6
Для каждого производителя, выпускающего ПК-блокноты c объёмом жесткого диска не менее 10 Гбайт, найти скорости таких ПК-блокнотов. Вывод: производитель, скорость.
Select maker, speed  from Product inner join Laptop on Product.model = Laptop.model   
where hd >= 10

7
https://sql-ex.ru/learn_exercises.php?LN=7
Найдите номера моделей и цены всех имеющихся в продаже продуктов (любого типа) производителя B (латинская буква).
Select laptop.model , laptop.price  from laptop inner join product on laptop.model = product.model  
where product.maker= 'B' 
union 
Select pc.model , pc.price from pc inner join product on pc.model = product.model  
where product.maker= 'B' 
union 
Select printer.model , printer.price from printer inner join product on printer.model = product.model  
where product.maker= 'B'

8
https://sql-ex.ru/learn_exercises.php?LN=8
Найдите производителя, выпускающего ПК, но не ПК-блокноты.
select maker from product where type='PC' and maker not in   
( select maker from product where type = 'Laptop') group by maker

9
https://sql-ex.ru/learn_exercises.php?LN=9
Найдите производителей ПК с процессором не менее 450 Мгц. Вывести: Maker
Select maker  from pc inner join product on pc.model = product.model where speed >= 450 
group by maker

10
https://sql-ex.ru/learn_exercises.php?LN=10
Найдите модели принтеров, имеющих самую высокую цену. Вывести: model, price
select model, price  from printer where price = (select max(price) from printer)

11
https://sql-ex.ru/learn_exercises.php?LN=11
Найдите среднюю скорость ПК.
select avg (speed) from pc

12
https://sql-ex.ru/learn_exercises.php?LN=12
Найдите среднюю скорость ПК-блокнотов, цена которых превышает 1000 дол.
Select avg(speed) from laptop where price > 1000 

13
https://sql-ex.ru/learn_exercises.php?LN=13

14
https://sql-ex.ru/learn_exercises.php?LN=14

15
https://sql-ex.ru/learn_exercises.php?LN=15

16
https://sql-ex.ru/learn_exercises.php?LN=16

17
https://sql-ex.ru/learn_exercises.php?LN=17

18
https://sql-ex.ru/learn_exercises.php?LN=18

19
https://sql-ex.ru/learn_exercises.php?LN=19

20
https://sql-ex.ru/learn_exercises.php?LN=20
