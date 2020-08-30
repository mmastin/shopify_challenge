# Shopify Data Science Challenge

> Sneaker Stores Average Order Value Outliers

![Full data exploration & analysis Jupyter Notebook here](https://github.com/mmastin/shopify_challenge/blob/master/data_exploration.ipynb)

From both the Sneaker Shop AOV problem description and a statistical summary of the dataset, it's clear that there are some large outlier orders skewing the AOV mean upwards. The simplest metric to use to improve insight into the value of a normal would be to use median (or 50% percentile value) in lieu of mean - or $284/per order. 

But the simplest solution doesn't help determine why exactly the mean is so much higher!


*Original Descriptive Statistics*

![Stats](https://github.com/mmastin/shopify_challenge/blob/master/Images/original_stats.png)


I created an additional feature, 'avg_shoe_cost,' to figure out the cause of the discrepancy.

Using Python, Pandas, NumPy, and Matplotlib, I was able to determine two direct causes:
- There are 17 total orders of 2,000 items for $704,000, vastly larger than all others. Strangely, they all occur at exactly 4am on different days. These are possibly wholesale distribution orders to a large client or a data encoding error. 
- There are 46 orders of a sneaker that costs $25,725, while no other sneaker in the dataset cost over $1,000. From some additional research, these are possibly an incredibly rare sneaker such as the DJ Khaled x Air Jordan 3 'Grateful' or Auto-Lacing Nike Mag.

By removing only these two extreme outliers from the dataset, I was able to get a clear picture of the other 98.7% of orders. The AOV is now $302.58 - quite close to the original median of $284.

In my opinion, the new AOV is a better metric to use for this analysis than median, because it incorporates information from the majority of expensive orders and shoes. 

It would also be possible to use methods such as Z-scores and Interquartile Range (IQR) to limit the effects of outliers on the analysis.


*Final Descriptive Statistics Without Outliers*

![Stats](https://github.com/mmastin/shopify_challenge/blob/master/Images/cleaned_stats.png)


*Final Scatter Plot of Data*

![Stats](https://github.com/mmastin/shopify_challenge/blob/master/Images/final_scatter.png)


# SQL Queries

> How many orders were shipped by Speedy Express in total?

```sql
// SELECT Count(*) FROM Orders
INNER JOIN Shippers ON Orders.ShipperID=Shippers.ShipperID
WHERE Shippers.ShipperName='Speedy Express';

Result: 54
```

> What is the last name of the employee with the most orders?

```sql
//SELECT Top 1 Employees.LastName
FROM Employees
INNER JOIN Orders ON Employees.EmployeeID=Orders.EmployeeID
GROUP BY Employees.LastName
ORDER BY Count(Employees.LastName) DESC

Result: Peacock
```

>What product was ordered the most by customers in Germany?

```sql
//SELECT Top 1 Products.ProductName
FROM ((Products
  INNER JOIN OrderDetails ON Products.ProductID=OrderDetails.ProductID)
  INNER JOIN Orders ON OrderDetails.OrderID=Orders.OrderID)
  INNER JOIN Customers ON Orders.CustomerID=Customers.CustomerID
WHERE Customers.Country='Germany'
GROUP BY Products.ProductName
ORDER BY SUM(OrderDetails.Quantity) DESC;

Result: Boston Crab Meat
```
