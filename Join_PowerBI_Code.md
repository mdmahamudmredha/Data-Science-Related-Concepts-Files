SELECT * FROM session-469016.Join_PowerBI.fact_sales;

SELECT * FROM session-469016.Join_PowerBI.dim_product;

SELECT * FROM session-469016.Join_PowerBI.dim_customer;

--Left Join
SELECT 
  s.amount,
  c.customer_name,
  c.region
FROM `Join_PowerBI.fact_sales` AS s LEFT JOIN 
`Join_PowerBI.dim_customer` AS c ON s.customer_id = c.customer_id;


-- Group By (Sub Query)
SELECT 
  region,
  SUM(amount) AS total_amount
FROM(SELECT 
  s.amount,
  c.customer_name,
  c.region
FROM `Join_PowerBI.fact_sales` AS s LEFT JOIN 
`Join_PowerBI.dim_customer` AS c ON s.customer_id = c.customer_id)
GROUP BY region
HAVING total_amount>1100;

-- Group By (CTE - Common Table Expression)
WITH sbr AS(SELECT 
  s.amount,
  c.customer_name,
  c.region
FROM `Join_PowerBI.fact_sales` AS s LEFT JOIN 
`Join_PowerBI.dim_customer` AS c ON s.customer_id = c.customer_id)
SELECT 
  region,
  SUM(amount) AS total_amount
FROM sbr
GROUP BY region
HAVING total_amount>1100;
