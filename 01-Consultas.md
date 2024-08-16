``` sql:

-- Consultas 

 use northwind;

-- Seleccionar todos los productos
select * from Products
-- Seleccionar todos los productos, 
-- pero que solo muestre los encabezados 
-- (proyección) nombre del producto, precio unitario,
-- cantidad de productos
select ProductName, UnitPrice, UnitsInStock 
from Products

-- Seleccionar todos los productos, 
-- pero que solo muestre los encabezados 
-- (proyección) nombre del producto, precio unitario,
-- cantidad de productos, pero los nombres
-- deben estar en español (Alias de Columna)

select ProductName As [Nombre Producto],
UnitPrice as 'Precio Unitario', 
UnitsInStock  Existencia 
from Products

-- Seleccionar todos aquellos productos
-- Donde el precio es igual a 18
select * from 
products 
where UnitPrice = 18.0

-- Seleccionar todos aquellos productos
-- Donde el precio es igual a 18, pero no deben
-- exceder las 30 unidades en stock
select ProductName As [Nombre Producto],
UnitPrice as 'Precio Unitario', 
UnitsInStock  Existencia 
from Products
where UnitsInStock<=30 and 
      UnitPrice = 18

-- seleccionar todos los productos 
-- donde los precios esten entre 18 y 23
-- y que precio unitario no sea 18
select ProductName As [Nombre Producto],
UnitPrice as 'Precio Unitario', 
UnitsInStock  Existencia 
from Products
where UnitPrice >18 and UnitPrice <=23

select ProductName As [Nombre Producto],
UnitPrice as 'Precio Unitario', 
UnitsInStock  Existencia 
from Products
where UnitPrice >=18 and UnitPrice <=23
      and UnitPrice <> 18

select ProductName As [Nombre Producto],
UnitPrice as 'Precio Unitario', 
UnitsInStock  Existencia 
from Products
where UnitPrice >=18 and UnitPrice <=23
      and not(UnitPrice = 18)

-- Seleccionar todas las ordenes de comprar
-- mostrando las fecha de compra, el numero
-- empleado, numero cliente, y mostrar también
-- la orden de compra, en año, mes y dia

select OrderDate as 'Fecha Compra', 
EmployeeID as 'Numero Empleado', 
CustomerID as 'Numero Cliente',
datepart(YEAR,OrderDate) as 'Año', 
datepart(MONTH,orderDate) as 'Mes',
datepart (day,OrderDate) as 'Dia'
from Orders

-- Seleccionar todas las ordenes de comprar
-- mostrando las fecha de compra, el numero
-- empleado, numero cliente, y mostrar también
-- la orden de compra, en año, mes y dia, y 
-- tambien para el año 1996, 1998, 2024
select OrderDate as 'Fecha Compra', 
EmployeeID as 'Numero Empleado', 
CustomerID as 'Numero Cliente',
datepart(YEAR,OrderDate) as 'Año', 
datepart(MONTH,orderDate) as 'Mes',
datepart (day,OrderDate) as 'Dia'
from Orders
where datepart(year,OrderDate) = 1996 
or datepart(year,OrderDate) = 1998
or datepart(year,OrderDate) = 2024 
order by 'Año' desc

select OrderDate as 'Fecha Compra', 
EmployeeID as 'Numero Empleado', 
CustomerID as 'Numero Cliente',
datepart(YEAR,OrderDate) as 'Año', 
datepart(MONTH,orderDate) as 'Mes',
datepart (day,OrderDate) as 'Dia'
from Orders
where datepart(year,OrderDate) = 1996 
or datepart(year,OrderDate) = 1998
or datepart(year,OrderDate) = 2024 
order by 4 desc

select OrderDate as 'Fecha Compra', 
EmployeeID as 'Numero Empleado', 
CustomerID as 'Numero Cliente',
datepart(YEAR,OrderDate) as 'Año', 
datepart(MONTH,orderDate) as 'Mes',
datepart (day,OrderDate) as 'Dia'
from Orders
where datepart(year,OrderDate) = 1996 
or datepart(year,OrderDate) = 1998
or datepart(year,OrderDate) = 2024 
order by datepart(YEAR,OrderDate) desc

-- seleccionar todos los productos 
-- donde los precios esten entre 18 y 23
-- (between)
select ProductName As [Nombre Producto],
UnitPrice as 'Precio Unitario', 
UnitsInStock  Existencia 
from Products
where UnitPrice between 18 and 23

-- Seleccionar las ordenes que se realizaron
-- entre 1996 y 1998
select * from 
Orders 
where DATEPART(year, OrderDate) 
between 1996 and 1998

-- Seleccionar las ordenes que se realizaron
-- entre 1996 y 1998, pero solamente aquellos
-- donde region de envio no sea null

select * from 
Orders 
where DATEPART(year, OrderDate) 
between 1996 and 1998
and ShipRegion is not null

-- seleccionar todas las ordenes 
-- para el pais de envio Estados unidos, 
-- Brazil y Mexico

select * from 
Orders 
where ShipCountry = 'usa' or
      ShipCountry = 'brazil'
	  or ShipCountry = 'mexico'

select * from 
Orders 
where ShipCountry in ('mexico', 'usa', 'brazil')

-- Funcionales de agregado (sum, avg, count(*),
-- count(columna), max, min)
-- La funciones de agregado solo dan como resultado,
-- un solo registro

-- cuantas ordenes de compra se realizaron en
-- 1996

select count(*) as 'Total de Ordenes'
from orders
where DATEPART(year, OrderDate) = 1996
```