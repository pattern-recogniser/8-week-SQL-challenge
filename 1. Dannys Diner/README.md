# 🍜 Danny's Diner

Danny started a diner, and has collected data about his customers and the items they have ordered. 

He plans on using these insights to help him decide whether he should expand the existing customer loyalty program - additionally he needs help to generate some basic datasets so his team can easily inspect the data without needing to use SQL.

Danny has provided you with a sample of his overall customer data due to privacy issues - but he hopes that these examples are enough for you to write fully functioning SQL queries to help him answer his questions!

## Questions and Answers

### 1. What is the total amount each customer spent at the restaurant?

```sql
SELECT sales.customer_id, 
	sum(menu.price) as total_spent
FROM
	dannys_diner.sales
INNER JOIN dannys_diner.menu
ON sales.product_id = menu.product_id
GROUP BY sales.customer_id
```

#### Result:

| customer_id | total_spent |
|-------------|-------------|
| A           |          76 |
| B           |          74 |
| C           |          36 |

- Customer A spent $74.
- Customer B spent $74.
- Customer C spent $36.

### 2. How many days has each customer visited the restaurant?
```sql
SELECT customer_id, 
	COUNT(distinct order_date) as days_visited
FROM
	dannys_diner.sales
GROUP BY customer_id;
```

#### Result:
| customer_id | days_visited |
|-------------|--------------|
| A           | 4            |
| B           | 6            |
| C           | 2            |
The date range for this data is from `2021-01-01` to `2021-02-01`. In the span of 30 days:
 - Customer A has visited 4 times.
 - Customer B has visited 6 times.
 - Customer C has visited 2 times. 
