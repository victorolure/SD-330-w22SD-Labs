1.
SELECT COUNT(DISTINCT CustomerID) AS 'Total Customers', 
(SELECT COUNT ( DISTINCT Name) FROM Sales.Store) AS 'Total Companies'
FROM Sales.Customer

2.
SELECT (CAST(COUNT(AddressLine2) AS FLOAT) /
		CAST(COUNT(*) AS FLOAT)
		) * 100 AS 'Percentage of Addresses with Address Line 2',
CountryRegionCode
FROM Person.Address
LEFT JOIN Person.StateProvince ON Person.StateProvince.StateProvinceID = Person.Address.StateProvinceID
GROUP BY CountryRegionCode

3.
SELECT AVG(StandardCost) AS 'Average StandardCost', AVG(ListPrice) AS 'Average ListPrice', Color
FROM Production.Product
WHERE FinishedGoodsFlag = 0
GROUP BY Color

4.
SELECT COUNT(DISTINCT SUBSTRING(ProductNumber, 1, 2) ) AS 'Number of Unique Prefixes'
FROM Production.Product
WHERE ProductNumber like '__-%'

5.
SELECT AVG(Weight) AS 'Averge Weight', Size From Production.Product
Group By Size
ORDER BY Size Desc

6.
SELECT  COUNT(SalesOrderID) AS 'Number Of Orders', CustomerID, 
(SELECT COUNT(DISTINCT CustomerID)   FROM Sales.SalesOrderHeader) AS 'Number Of Customers In SalesOrder'
FROM Sales.SalesOrderHeader
GROUP BY CustomerID

7.
SELECT COUNT(DISTINCT rowguid) AS 'Number of Unique RowGuiDs',
COUNT(rowguid) AS 'Total Count of GuiDs'
FROM Sales.Customer