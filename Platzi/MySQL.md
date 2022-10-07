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