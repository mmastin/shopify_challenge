# Shopify Data Science Challenge

> Sneaker Stores Average Order Value Outliers

![Full data exploration & analysis Jupyter Notebook here](https://github.com/mmastin/shopify_challenge/blob/master/data_exploration.ipynb)

From both the Sneaker Shop AOV problem description and a statistical summary of the dataset, it's clear that there are some large outlier orders skewing the AOV mean upwards. 

![Stats](https://github.com/mmastin/shopify_challenge/blob/master/Images/original_stats.png)
*Original Descriptive Statistics*


![Stats](https://github.com/mmastin/shopify_challenge/blob/master/Images/cleaned_stats.png)
*Final Descriptive Statistics Without Outliers*


![Stats](https://github.com/mmastin/shopify_challenge/blob/master/Images/final_scatter.png)
*Final Scatter Plot of Data*


# SQL Queries

> How many orders were shipped by Speedy Express in total?

```sql
// SELECT Count(*) FROM Orders
INNER JOIN Shippers ON Orders.ShipperID=Shippers.ShipperID
WHERE Shippers.ShipperName='Speedy Express';

54
```

> What is the last name of the employee with the most orders?

```sql
//SELECT Employees.LastName
FROM Employees
INNER JOIN Orders Employees.EmployeeID=Orders.EmployeeID

```

>What product was ordered the most by customers in Germany?

```sql
//

```
