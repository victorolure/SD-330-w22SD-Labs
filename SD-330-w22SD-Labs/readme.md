1.
SELECT *, 
CASE WHEN Name LIKE 'HL%' THEN 'Happy Locomotion Holdings'
	WHEN Name LIKE 'Men%' OR Name LIKE 'Women%' THEN 'Human Garments'
	ELSE Name
	END AS 'Product Info'
FROM Production.Product

2.
SELECT * FROM Production.Product
WHERE ProductSubcategoryID IN (
SELECT ProductSubcategoryID FROM Production.ProductSubcategory
WHERE ProductCategoryID = 3)

4.
SELECT DISTINCT Name From Production.Product
WHERE ProductID IN 
(SELECT ProductID FROM Sales.SalesOrderDetail
WHERE OrderQty > 5)

5.
SELECT Name, ListPrice FROM Production.Product
WHERE ListPrice > (SELECT ListPrice From Production.Product
WHERE ProductNumber = 'FR-R72R-60')
ORDER BY ListPrice ASC

6.
SELECT *,ListPrice-StandardCost AS 'Markup' FROM Production.Product
ORDER BY Markup DESC