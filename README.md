# Anna_Onuszczuk_Data_Krakow
Solving the task for Data Analyst Intern position 


## Query used for solving the first task

```
SELECT
  op.product_id AS productId,               -- Select the product ID from the orders_products table and assign it to the alias 'productId'
  p.weight * op.quantity AS totalWeight     -- Multiply the product weight from the products table by the quantity from the orders_products table and assign the result to the alias 'totalWeight'
FROM
  orders AS o                               -- Select data from the 'orders' table and alias it as 'o'
  JOIN route_segments AS rs                  -- Join the 'route_segments' table and alias it as 'rs'
  JOIN orders_products AS op                 -- Join the 'orders_products' table and alias it as 'op'
  JOIN products AS p                         -- Join the 'products' table and alias it as 'p'
WHERE
  rs.order_id = o.order_id                  -- Connect data from the 'route_segments' table with data from the 'orders' table based on the order ID
  AND o.order_id = op.order_id               -- Connect data from the 'orders' table with data from the 'orders_products' table based on the order ID
  AND p.product_id = op.product_id           -- Connect data from the 'products' table with data from the 'orders_products' table based on the product ID
  AND o.customer_id = 32                     -- Select only orders from the customer with ID 32
  AND rs.segment_end_time < STR_TO_DATE ("February 14 2024", "%M %d %Y")  -- Select only route segments with end time earlier than February 14, 2024
  AND rs.segment_end_time > STR_TO_DATE ("February 12 2024", "%M %d %Y")  -- Select only route segments with end time later than February 12, 2024
ORDER BY
  totalWeight ASC                           -- Sort the results in ascending order based on the 'totalWeight' field

```
