# TechTFQ_SQL_Interview_Query_19

PROBLEM STATEMENT: Given table showcases details of pizza delivery order for the year of 2023.
If an order is delayed then the whole order is given for free. Any order that takes 30 minutes more than the order time is considered as delayed order. 
Identify the percentage of delayed order for each month and also display the total no of free pizzas given each month.

```sql

DROP TABLE IF EXISTS pizza_delivery;

CREATE TABLE pizza_delivery (order_id INT, 
							 order_time TIMESTAMP, 
							 expected_delivery TIMESTAMP, 
							 actual_delivery TIMESTAMP, 
							 no_of_pizzas INT, 
							 price DECIMAL(6,2)); 
COPY pizza_delivery (order_id, 
					 order_time, 
					 expected_delivery, 
					 actual_delivery, 
					 no_of_pizzas, 
					 price) 
			FROM '/Users/Karl/Documents/Q19_dataset.CSV' DELIMITER ',' CSV HEADER;


SELECT * FROM pizza_delivery
LIMIT 10;

```

| order_id | order_time | expected_delivery | actual_delivery | no_of_pizzas | price |
|----------|------------|-------------------|-----------------|--------------|-------|
| 1	 | 2023-09-29 21:22:57 | 2023-09-29 21:52:57 | 2023-09-29 21:52:57 |	8	| 59.25 |
| 2	 | 2023-06-03 19:32:40 | 2023-06-03 20:02:40 | 2023-06-03 20:02:40 | 2	| 82.56 |
| 3	| 2023-03-19 18:14:04 | 2023-03-19 18:44:04 | 2023-03-19 18:44:04 |	5	| 77.70 |
| 4	 | 2023-06-21 18:45:00 | 2023-06-21 19:15:00 | 2023-06-21 19:15:00 |	3 |	71.10 |
| 5	 | 2023-11-16 20:24:03 | 2023-11-16 20:54:03 | 2023-11-16 20:54:03 |	1	 | 72.74 |
| 6	| 2023-06-01 00:17:54 | 2023-06-01 00:47:54 | 2023-06-01 00:47:54 |	9	| 62.01 |
| 7	| 2023-04-15 15:29:57 | 2023-04-15 15:59:57 | 2023-04-15 15:59:57 | 8	| 59.82 |
| 8	| 2023-11-03 12:35:06 | 2023-11-03 13:05:06 | 2023-11-03 13:05:06 |	5	| 95.90 |
| 9	| 2023-01-20 21:36:56 | 2023-01-20 22:06:56 | 2023-01-20 22:06:56 | 6	| 52.15 |
| 10	 | 2023-07-31 13:43:39 | 2023-07-31 14:13:39 | 2023-07-31 14:13:39 | 10	| 81.69 |

