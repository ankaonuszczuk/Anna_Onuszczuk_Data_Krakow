# Anna_Onuszczuk_Data_Krakow
Solving the task for Data Analyst Intern position 


## Query used for solving the first task

```
SELECT
  op.product_id AS productId,
  p.weight * op.quantity AS totalWeight
FROM
  orders AS o
  JOIN route_segments AS rs
  JOIN orders_products AS op
  JOIN products AS p
WHERE
  rs.order_id = o.order_id 
  AND o.order_id = op.order_id
  AND p.product_id = op.product_id
  AND o.customer_id = 32
  AND rs.segment_end_time < STR_TO_DATE ("February 14 2024", "%M %d %Y")
  AND rs.segment_end_time > STR_TO_DATE ("February 12 2024", "%M %d %Y")
ORDER BY
  totalWeight ASC

  -- order the result 
```
