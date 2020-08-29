# Shopify Data Science Challenge

> Subtitle or Short Description Goes Here

![Full data exploration & analysis Jupyter Notebook here](https://github.com/mmastin/shopify_challenge/blob/master/data_exploration.ipynb)


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
