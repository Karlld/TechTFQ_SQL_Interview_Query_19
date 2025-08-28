```sql

WITH late_delivery AS(SELECT order_id,
					         TO_CHAR(order_time, 'MON-YY') AS order_month,
					         DATE_TRUNC('month', order_time) AS order_month_date,
					        CASE WHEN (actual_delivery - order_time) > '00:30:00' THEN 1 ELSE 0 END AS late,
					        CASE WHEN (actual_delivery - order_time) > '00:30:00' THEN no_of_pizzas ELSE 0 END AS late_pizza
	                     FROM pizza_delivery
					 )
		SELECT order_month,
		       CONCAT((ROUND(100*SUM(late)/COUNT(order_id)::DECIMAL(4,2),2)::VARCHAR(6)),'%'),
			   SUM(late_pizza) AS late_pizzas
			FROM late_delivery
			GROUP BY order_month, order_month_date
			ORDER BY order_month_date ASC;
    
```

| period | delayed_delivery_perc | free_pizzas |
|--------|-----------------------|-------------|
| JAN-23 | 8.70% |	31 |
| FEB-23 | 11.83% |	49 |
| MAR-23 | 15.00% | 61 |
| APR-23 | 13.10% |	77 |
| MAY-23 | 14.12% |	65 |
| JUN-23 | 10.00% |	48 |
| JUL-23 | 15.07% | 43 |
| AUG-23 | 10.75% |	63 |
| SEP-23 | 16.87% |	89 |
| OCT-23 | 15.05% | 60 |
| NOV-23 | 21.65% |	105 |
| DEC-23 | 14.29% | 58 |
