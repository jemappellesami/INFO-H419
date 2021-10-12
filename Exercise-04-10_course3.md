# Exercice : multidimensional databases
The given schema is still an operationnal databse. We can execute classical SQL queries, aggregate operations, etc. **<span style='color:#81FFF2'>but</span>** it is certainly not optimal.


## Ex 1

    select category, country, sum(quantity) as 'TotalQty'

    from "Order Details" Od
        inner join Orders O on Od.OrderID = O.OrderID
        inner join Customers C on O.CustomerID = C.CustomerID
        inner join Products P.ProductID = Od.ProductID

    group by (category, country)


## Ex 2
    SELECT TOP 3 CA.CategoryName
    FROM "Order Details" OD
        
        INNER JOIN Product P
            ON P.ProductID = OD.ProductID

        INNER JOIN Category CA
            ON CA.CategoryID = P.CategoryID

    GROUP BY CA.CategoryName
    ORDER BY SUM(OD.Quantity*OD.UnitPrice*(1-OD.Discount)) DESC