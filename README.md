Project Overview :-

This project analyzes pizza sales data using SQL to extract meaningful business insights. The goal is to identify key sales metrics
such as total orders, revenue, and popular pizza types, sizes, and categories. Advanced SQL techniques, including joins, grouping, 
and aggregate functions, are applied to understand order distribution and revenue trends.

 Key Objectives :-

1.Retrieve the total number of orders placed.

2.Calculate the total revenue generated from pizza sales.

3.Identify the highest-priced pizza.

4.Determine the most common pizza size ordered.

5.List the top 5 most ordered pizza types along with their quantities.

6.Find the total quantity of each pizza category ordered using joins.

7.Analyze order distribution by hour of the day.

8.Calculate the average number of pizzas ordered per day.

9.Identify the top 3 most ordered pizza types based on revenue.

10.Analyze cumulative revenue trends over time.

11.Find the top 3 most ordered pizza types for each pizza category.

Technologies & Tools Used :-

->SQL (for data extraction, transformation, and analysis)

->Database Management System ( MySQL )

->Canvas (for project documentation and query presentation)

 Project Structure :-

->SQL Queries: Scripts to perform various analyses on pizza sales data.

->Database Schema: Tables and relationships used in the project.

->Results & Insights: Key findings derived from SQL queries.

 SQL Queries :-

 -- Retrieve the total number of orders
SELECT COUNT(DISTINCT order_id) AS total_orders FROM orders;

-- Calculate the total revenue generated from pizza sales
SELECT SUM(price * quantity) AS total_revenue FROM order_details;

-- Identify the highest-priced pizza
SELECT name, price FROM pizzas ORDER BY price DESC LIMIT 1;

-- Determine the most common pizza size ordered
SELECT size, COUNT(*) AS order_count FROM pizzas GROUP BY size ORDER BY order_count DESC LIMIT 1;

-- List the top 5 most ordered pizza types along with their quantities
SELECT pizza_type, SUM(quantity) AS total_quantity FROM order_details GROUP BY pizza_type ORDER BY total_quantity DESC LIMIT 5;

-- Find the total quantity of each pizza category ordered
SELECT category, SUM(quantity) AS total_quantity FROM pizzas INNER JOIN order_details ON pizzas.id = order_details.pizza_id GROUP BY category;

-- Analyze order distribution by hour of the day
SELECT HOUR(order_time) AS order_hour, COUNT(*) AS order_count FROM orders GROUP BY order_hour ORDER BY order_hour;

-- Calculate the average number of pizzas ordered per day
SELECT order_date, AVG(quantity) AS avg_pizzas FROM orders INNER JOIN order_details ON orders.id = order_details.order_id GROUP BY order_date;

-- Identify the top 3 most ordered pizza types based on revenue
SELECT pizza_type, SUM(price * quantity) AS total_revenue FROM pizzas INNER JOIN order_details ON pizzas.id = order_details.pizza_id GROUP BY pizza_type ORDER BY total_revenue DESC LIMIT 3;

-- Analyze cumulative revenue trends over time
SELECT order_date, SUM(price * quantity) OVER (ORDER BY order_date) AS cumulative_revenue FROM orders INNER JOIN order_details ON orders.id = order_details.order_id;

-- Find the top 3 most ordered pizza types for each pizza category
SELECT category, pizza_type, SUM(quantity) AS total_quantity FROM pizzas INNER JOIN order_details ON pizzas.id = order_details.pizza_id GROUP BY category, pizza_type ORDER BY category, total_quantity DESC;

 Conclusion :-

This project helps businesses understand customer preferences, optimize inventory, and improve sales strategies by leveraging data-driven insights.


