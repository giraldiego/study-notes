# La consola de MySQL
Connect to MySQL
`sudo mysql -u root -h localhost -p`

To show available databases:
`show databases;`

To start using a db:
`use database_name`

To know in what database we are:
`select database();`

# ¿Qué es una base de datos?

Es un lugar donde podemos ir almacenando datos puntuales de cualquier cantidad de cosas para después operar sobre esos datos y convertirlos en información. Esa información convertirla en operaciones de negocio y las operaciones de negocio convertirlas en dinero, crecimiento sabiduría lo que sea. **TODO RESIDE EN LOS DATOS Y CÓMO OPERAMOS SOBRE LOS DATOS**  

# Comando CREATE
Dos tipos de tablas por defecto en MySQL:  
•**MyISAM:** directa, sencilla, más rápida y las transacciones son completamente uno a uno:  
•**InnoDB:** nueva, recuperable en caso de falla de disco duro pero es un poco más lenta.

En la vida real usamos las tablas con dos propósitos:  
•**Catalogo:** crecerá en un orden lento, según las necesidades de la propia BD. (Listado de Usuarios, InnoDB)  
•**Operación:** se enfocan a lectura, mayor acceso a disco duro. (Prestamos de libros, MyISAM).

`CREATE DATABASE [IF NOT EXISTS] db_name;`

`SHOW warnings;`

**Cardinalidad:** Numero de elementos de la tabla.

```sql
CREATE TABLE IF NOT EXISTS books (
	book_id INTEGER UNSIGNED PRIMARY KEY AUTO_INCREMENT,
	author_id INTEGER UNSIGNED ,
	title VARCHAR(100) NOT NULL,
	year INTEGER UNSIGNED NOT NULL DEFAULT 1900,
	language VARCHAR(2) NOT NULL DEFAULT 'es' COMMENT 'ISO 639-1 Language',
	cover_url VARCHAR(500),
	price DOUBLE(6,2) NOT NULL DEFAULT 10.0,
	sellable TINYINT(1) DEFAULT 1,
	copies INTEGER NOT NULL DEFAULT 1,
	description TEXT
);

CREATE TABLE IF NOT EXISTS authors (
	author_id INTEGER UNSIGNED PRIMARY KEY AUTO_INCREMENT,
	name VARCHAR(100) NOT NULL,
	nationality VARCHAR(3)
);

CREATE TABLE clients (
	client_id INTEGER UNSIGNED PRIMARY KEY AUTO_INCREMENT,
	`name` VARCHAR(50) NOT NULL,
	email VARCHAR(100) NOT NULL UNIQUE,
	birthdate DATETIME,
	gender ENUM('M', 'F', 'ND') NOT NULL,
	active TINYINT(1) NOT NULL DEFAULT 1, 
	created_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
	updated_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);

CREATE TABLE IF NOT EXISTS operations (
	operation_id INTEGER UNSIGNED PRIMARY KEY AUTO_INCREMENT,
	book_id INTEGER UNSIGNED,
	client_id INTEGER UNSIGNED,
	type ENUM('prestado', 'devuelto', 'vendido') NOT NULL,
	created_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
	updated_at TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
	finished TINYINT(1) NOT NULL
);

```

`DROP TABLE authors;`
`DESCRIBE books;`
`SHOW FULL COLUMNS FROM books;`

-  EL no colocar AUTO_INCREMENT a la columna que es PRIMARY KEY simplemente vuelve el proceso de asignar id a una forma manual o se puede asignar desde otra capa de negocios.  
    UNIQUE, la columna que tenga el constraint unique garantiza que el valor que se guarda en esa columna sea único
    
-   TIMESTAMP  
    Está basado en el número epoch que es el 1 enero de 1970 hasta la fecha y es donde se determina el inicio de las computadoras y es un número entero que se guarda en segundos y permite hacer operaciones sobre el.
    
-   DATETIME  
    Este tipo de datos puede guardar cualquier valor de tipo fecha sin restricción. Incluso anterior a nuestra era. es por eso que las fechas de nacimiento de usuarios debe utilizar este valor para garantizar que podemos registrarlos con la fecha adecuada.
    
-  TIMESTAMP vs DATETIME: hay que resaltar que un, 1.TIMESTAMP “NO PUEDE HACER TODO LO DE DATETIME pero DATETIME SÍ PUEDE HACERLO DE UN TIMESTAMP”, 2.DATETIME no está guardado en segundos y no es tan eficiente para hacer cálculos.

# Comando INSERT

```sql
INSERT INTO authors(author_id, `name`, nationality)
VALUES(NULL,'Juan Rulfo','MEX');

INSERT INTO authors(`name`, nationality)
VALUES('Gabriel Garcia Marquez','COL');

INSERT INTO authors()
VALUES(NULL,'Juan Gabriel Vasquez','COL');
```

Multiple insertions:
```sql
INSERT INTO authors (name, nationality)
VALUES ('Julio Cortazar', 'ARG'),
('Isabel Allende','CHI'),
('Octavio Paz', 'MEX'),
('Juan Carlos Onetti', 'UY'); 
```

```sql
INSERT INTO `clients` (client_id, name, email, birthdate, gender, active) 
VALUES (1,'Maria Dolores Gomez','Maria Dolores.95983222J@random.names','1971-06-06','F',1),
(2,'Adrian Fernandez','Adrian.55818851J@random.names','1970-04-09','M',1),
(3,'Maria Luisa Marin','Maria Luisa.83726282A@random.names','1957-07-30','F',1),
(4,'Pedro Sanchez','Pedro.78522059J@random.names','1992-01-31','M',1);
```

Action when it finds a duplicate:
```sql
ON DUPLICATE KEY IGNOREALL -- Never use ever
ON DUPLICATE KEY UPDATE SET active = VALUES(active) -- Update 
```

Nice formatting:
```sql
select * from clients where client_id=4\G -- To show data formatted

```

Insert a record updating its values:
```sql
INSERT INTO `clients` ( name, email, birthdate, gender, active) 
VALUES ('Pedro Sanchez','Pedro.78522059J@random.names','1992-01-31','M',0) AS new
ON DUPLICATE KEY UPDATE active = new.active; 
```

```sql
INSERT INTO books (title, author_id)
VALUES('El Laberinto de la Soledad', 6);

INSERT INTO books (title, author_id, `year`)
VALUES('Vuelta al Laberinto de la Soledad',
	(SELECT author_id FROM authors
	WHERE name = 'Octavio Paz'
	LIMIT 1),
	1960	  
);

```

# Bash y archivos SQL
```bash
$ mysql -u root -p < all_schema.sql
$ mysql -u root -p -D cursoplatzi < all_data.sql
```

# SELECT

## Su Majestad

```sql
SELECT name, email, YEAR(NOW()) - YEAR(birthdate) AS edad, gender
FROM clients
WHERE gender = 'F'
	AND name LIKE '%Lop%'
```

## Comando JOIN

```sql
select * from authors where author_id >0 and author_id <= 5;
select book_id, author_id, title from books where author_id between 1 and 5;
```

```sql
SELECT b.book_id, a.name, a.author_id, b.title
FROM books AS b
JOIN authors as a
	ON a.author_id = b.author_id
WHERE a.author_id between 1 AND 5;
```

```sql
SELECT c.name, b.title, a.name AS author_name, t.type
FROM transactions AS t
JOIN books AS b
 ON t.book_id = b.book_id
JOIN clients AS c
 ON t.client_id = c.client_id
JOIN authors AS a
 ON a.author_id = b.author_id
WHERE c.gender = 'M'
 AND t.type IN ('sell', 'lend')
```

Alternative but not recommended:
```sql
SELECT b.title, a.name
FROM authors AS a, books AS b
WHERE a.author_id = b.author_id
LIMIT 10
```

## Left JOIN
```sql
SELECT a.author_id, a.name, a.nationality, b.title
FROM authors AS a
LEFT JOIN books AS b
 ON b.author_id = a.author_id 
WHERE a.author_id between 1 and 5
ORDER BY a.author_id
```

```sql
SELECT a.author_id, a.name, a.nationality, COUNT(b.book_id)
FROM authors AS a
LEFT JOIN books AS b
 ON b.author_id = a.author_id 
WHERE a.author_id between 1 and 5
GROUP BY a.author_id
ORDER BY a.author_id
```

## Tipos de JOIN

https://learnsql.com/blog/sql-join-cheat-sheet/joins-cheat-sheet-a4.pdf

![[Pasted image 20221007144414.png]]

# 5 casos de negocio

## Qué nacionalidades hay?

```sql
SELECT DISTINCT nationality FROM authors ORDER BY nationality;
```

## Cuantos escritores hay de cada nacionalidad excluyendo a Rusia y Austria
```sql
SELECT a.nationality, COUNT(a.author_id) as count_authors
FROM authors AS a
WHERE nationality IS NOT NULL
AND nationality NOT IN ('RUS', 'AUT')
GROUP BY a.nationality
ORDER BY count_authors DESC, a.nationality ASC;
```

```sql
-- 1. ¿Qué nacionalidades hay?
-- Mediante la clausula DISTINCT trae solo los elementos distintos
SELECT DISTINCT nationality 
FROM authors
ORDER BY 1;

-- 2. ¿Cuántos escritores hay de cada nacionalidad?
-- IS NOT NULL para traer solo los valores diferentes de nulo
-- NOT IN para traer valores que no sean los declarados (RUS y AUT)
SELECT nationality, COUNT(author_id) AS c_authors
FROM authors
WHERE nationality IS NOT NULL
	AND nationality NOT IN ('RUS','AUT')
GROUP BY nationality
ORDER BY c_authors DESC, nationality ASC;

--- 3. Cuantos libros hay de cada nacionalidad
SELECT a.nationality, COUNT(book_id) AS total 
FROM books AS b
JOIN authors AS a
 ON b.author_id = a.author_id
GROUP BY a.nationality
ORDER BY total DESC, a.nationality ASC
```

```sql
UPDATE books  
SET price = FLOOR(RAND()*(35-10+1))+10  
WHERE book_id between 1 and 198

-- 4. ¿Cuál es el promedio/desviación standard del precio de libros?
SELECT 
AVG(price) AS precio_prom, 
STDDEV(price) AS std_dev
FROM books

-- 5. ¿Cuál es el promedio/desviación standard del precio de libros por nacionalidad?
-- Agrupar por la columna pivot
SELECT a.nationality,
COUNT(b.book_id) AS libros,
AVG(price) AS precio_prom, 
STDDEV(price) AS std_dev
FROM books AS b
JOIN authors AS a
 ON b.author_id = a.author_id
GROUP BY a.nationality
ORDER BY libros DESC, precio_prom DESC

-- 6. ¿Cuál es el precio máximo/mínimo de un libro?
SELECT nationality, MAX(price), MIN(price)
FROM books AS b
JOIN authors AS a
  ON a.author_id = b.author_id
GROUP BY nationality;

-- 7. ¿cómo quedaría el reporte de préstamos?
-- CONCAT: para concatenar en cadenas de texto.
-- TO_DAYS: recibe un timestamp ó un datetime
SELECT c.name, t.type, b.title, 
CONCAT(a.name, "(", a.nationality, ")") AS author
FROM transactions AS t
LEFT JOIN clients AS c
  ON c.client_id = t.client_id
LEFT JOIN books AS b
  ON b.book_id = t.book_id
LEFT JOIN authors AS a
  ON a.author_id = b.author_id
```