1.
SELECT Sales.SalesOrderHeader.SalesOrderID, Sales.SalesOrderDetail.* FROM Sales.SalesOrderHeader
LEFT JOIN Sales.SalesOrderDetail
ON Sales.SalesOrderDetail.SalesOrderID = Sales.SalesOrderHeader.SalesOrderID

2.
SELECT Name, * FROM Sales.SalesOrderDetail
LEFT JOIN Production.Product
ON Sales.SalesOrderDetail.ProductID= Production.Product.ProductID
WHERE OrderQty >= 5

3.
SELECT Production.Product.Name, Production.Product.Weight FROM Production.Product
LEFT JOIN Production.ProductSubcategory
ON Production.Product.ProductSubcategoryID = Production.ProductSubcategory.ProductSubcategoryID
LEFT JOIN Production.ProductCategory
ON Production.ProductSubcategory.ProductCategoryID = Production.ProductCategory.ProductCategoryID
WHERE Production.ProductCategory.Name = 'Bikes'
AND Production.Product.Weight < 10000

4.
SELECT TotalDue, * FROM Sales.SalesOrderDetail
LEFT JOIN Sales.SalesOrderHeader
ON Sales.SalesOrderDetail.SalesOrderID = Sales.SalesOrderHeader.SalesOrderID

5.
SELECT DISTINCT AddressLine1, AddressLine2, City
,CustomerID
FROM Person.Address
LEFT JOIN Sales.SalesOrderHeader
ON Sales.SalesOrderHeader.BillToAddressID = Person.Address.AddressID

6.
SELECT DISTINCT AddressLine1, City
,COUNT(CustomerID) AS 'Number Of Customers'
FROM Person.Address
LEFT JOIN Sales.SalesOrderHeader
ON Sales.SalesOrderHeader.BillToAddressID = Person.Address.AddressID
GROUP BY AddressLine1, City
ORDER BY AddressLine1 ASC