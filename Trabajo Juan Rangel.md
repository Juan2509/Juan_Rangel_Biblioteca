# 			Trabajo Juan Rangel



## Normalización:

La base de datos fue normalizada hasta la Tercera Forma Normal (3FN).

En la Primera Forma Normal (1FN), se eliminaron atributos multivaluados, separando las categorías en una tabla independiente y evitando listas dentro de los campos.

En la Segunda Forma Normal (2FN), se garantizó que todos los atributos dependieran completamente de su clave primaria, especialmente en la tabla intermedia libro_categoria, la cual utiliza una clave compuesta sin atributos adicionales.

En la Tercera Forma Normal (3FN), se eliminaron dependencias transitivas, separando entidades como categorías y evitando redundancia de datos.

Como resultado, la base de datos presenta una estructura organizada y sin redundancia.



## Modelo Físico:

### 	`Libros:`

`CREATE TABLE libros (`
    `id_libro INT PRIMARY KEY AUTO_INCREMENT,`
    `isbn VARCHAR(20) UNIQUE,`
    `titulo VARCHAR(100),`
    `anio INT,`
    `genero VARCHAR(50)`
`);`

	### 	Usuarios:

`CREATE TABLE usuarios (`
    `id_usuario INT PRIMARY KEY AUTO_INCREMENT,`
    `nombre VARCHAR(100),`
    `email VARCHAR(100) UNIQUE,`
    `telefono VARCHAR(20),`
    `fecha_registro DATE`
`);`

### 	Préstamos:

`CREATE TABLE prestamos (`
    `id_prestamo INT PRIMARY KEY AUTO_INCREMENT,`
    `id_usuario INT NOT NULL,`
    `id_copia INT,`
    `fecha_prestamo DATE,`
    `fecha_devolucion DATE,`
    `FOREIGN KEY (id_usuario) REFERENCES usuarios(id_usuario),`
    `FOREIGN KEY (id_copia) REFERENCES copias(id_copia)`
`);`

### 	Reseñas:

`CREATE TABLE resenas (`
    `id_resena INT PRIMARY KEY AUTO_INCREMENT,`
    `id_usuario INT,`
    `id_libro INT,`
    `calificacion INT,`
    `comentario TEXT,`
    `fecha DATE,`
    `FOREIGN KEY (id_usuario) REFERENCES usuarios(id_usuario),`
    `FOREIGN KEY (id_libro) REFERENCES libros(id_libro)`
`);`

### 	Categorías:

`CREATE TABLE categorias (`
    `id_categoria INT PRIMARY KEY AUTO_INCREMENT,`
    `nombre VARCHAR(100)`
`);`

### 	Libro Categoría:

`CREATE TABLE libro_categoria (`
    `id_libro INT,`
    `id_categoria INT,`
    `PRIMARY KEY (id_libro, id_categoria),`
    `FOREIGN KEY (id_libro) REFERENCES libros(id_libro),`
    `FOREIGN KEY (id_categoria) REFERENCES categorias(id_categoria)`
`);`



## SCRIPT SQL:


`CREATE DATABASE biblioteca;`
`USE biblioteca;`


`CREATE TABLE libros (`
    `id_libro INT AUTO_INCREMENT PRIMARY KEY,`
    `isbn VARCHAR(20) UNIQUE,`
    `titulo VARCHAR(100),`
    `anio INT,`
    `genero VARCHAR(50)`
`);`


`CREATE TABLE usuarios (`
    `id_usuario INT AUTO_INCREMENT PRIMARY KEY,`
    `nombre VARCHAR(100),`
    `email VARCHAR(100) UNIQUE,`
    `telefono VARCHAR(20),`
    `fecha_registro DATE`
`);`


`CREATE TABLE categorias (`
    `id_categoria INT AUTO_INCREMENT PRIMARY KEY,`
    `nombre VARCHAR(100)`
`);`


`CREATE TABLE copias (`
    `id_copia INT AUTO_INCREMENT PRIMARY KEY,`
    `id_libro INT,`
    `estado VARCHAR(20),`
    `FOREIGN KEY (id_libro) REFERENCES libros(id_libro)`
`);`


`CREATE TABLE prestamos (`
    `id_prestamo INT AUTO_INCREMENT PRIMARY KEY,`
    `id_usuario INT NOT NULL,`
    `id_copia INT,`
    `fecha_prestamo DATE,`
    `fecha_devolucion DATE,`
    `FOREIGN KEY (id_usuario) REFERENCES usuarios(id_usuario),`
    `FOREIGN KEY (id_copia) REFERENCES copias(id_copia)`
`);`


`CREATE TABLE resenas (`
    `id_resena INT AUTO_INCREMENT PRIMARY KEY,`
    `id_usuario INT,`
    `id_libro INT,`
    `calificacion INT,`
    `comentario TEXT,`
    `fecha DATE,`
    `FOREIGN KEY (id_usuario) REFERENCES usuarios(id_usuario),`
    `FOREIGN KEY (id_libro) REFERENCES libros(id_libro)`
`);`


`CREATE TABLE libro_categoria (`
    `id_libro INT,`
    `id_categoria INT,`
    `PRIMARY KEY (id_libro, id_categoria),`
    `FOREIGN KEY (id_libro) REFERENCES libros(id_libro),`
    `FOREIGN KEY (id_categoria) REFERENCES categorias(id_categoria)`
`);`



## 3 Consultas básicas de SQL:

### 	1. Ver libros disponibles:

`SELECT l.titulo, c.id_copia, c.estado`
`FROM libros l`
`JOIN copias c ON l.id_libro = c.id_libro`
`WHERE c.estado = 'disponible';`

### 	2. Préstamos de un usuario:

`SELECT u.nombre, p.id_prestamo, p.fecha_prestamo, p.fecha_devolucion`
`FROM usuarios u`
`JOIN prestamos p ON u.id_usuario = p.id_usuario`
`WHERE u.id_usuario = 1;`

### 	3. Reseñas de un libro:

`SELECT l.titulo, r.calificacion, r.comentario, r.fecha`
`FROM libros l`
`JOIN resenas r ON l.id_libro = r.id_libro`
`WHERE l.id_libro = 1;`





## Diagrama de flujo

<a href="https://ibb.co/Tx56M5dk"><img src="https://i.ibb.co/Pv8KG80N/image.png" alt="image" border="0"></a>

## Modelo Lógico

<a href="https://ibb.co/qFY5RcLD"><img src="https://i.ibb.co/VpYmvz0L/image.png" alt="image" border="0"></a>