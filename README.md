# Простые SQL запросы

### Запрос "Вывести все записи таблицы":
SELECT * FROM customer


### Запрос "Вывести количество записей в таблице":
SELECT COUNT(*)                             
FROM customer


### Запрос "Вывести определенные столбцы из таблицы":
SELECT last_name, first_name                         
FROM customer


### Запрос "Количество товара в категории":
SELECT category_id as category, count(*) AS cnt                   
FROM product                    
GROUP BY category_id                             


### Запрос "Количество платежей":
select count(*)                     
from orders  


### Запроc "В какой категории находится больше всего товаров":
SELECT category as "категории", count(*) AS "количество"             
FROM product                        
JOIN category on product.category_id = category.category_id                 
group by category.category_id                     
order by count(*) desc                         
limit 1


### Запроc "С кем живет Williams Linda":
select s.last_name, s.first_name                  
from customer c                    
join staff s on c.address_id = s.address_id                     
where c.last_name ='Williams' and c.first_name ='Linda'


### Запроc "Найти сумму платежей пользователей, чья фамилия начинается на А":
 SELECT customer_id, SUM(amount)               
 FROM orders                   
 WHERE customer_id in (                   
 	SELECT customer_id               
 	FROM customer              
 	WHERE LEFT(last_name, 1) = 'A')               
 GROUP BY customer_id

