[README.md](https://github.com/user-attachments/files/27442055/README.md)
# 📚 Sistema de Biblioteca Digital - ReadFlow

## 📌 Información General

**Nombre:** [TuNombre_TuApellido_Biblioteca]
**Modalidad:** Individual
**Herramientas utilizadas:** draw.io, drawsql, Programiz SQL, GitHub

------

## 🧠 Contexto

La empresa ReadFlow presenta problemas en la gestión de su información, como desorganización de datos, dificultad en el control de préstamos, pérdida de información de usuarios y desconocimiento de la disponibilidad de libros.

Este proyecto busca solucionar estos problemas mediante el diseño de una base de datos estructurada.

------

## 🎯 Objetivo

Diseñar una base de datos completa que permita gestionar:

- Libros
- Usuarios
- Préstamos
- Reseñas
- Categorías

Incluyendo todas las etapas:

- Modelo conceptual
- Modelo lógico
- Normalización (3FN)
- Modelo físico

------

## 🧩 Modelo Conceptual

Se diseñó un diagrama Entidad-Relación (E-R) que representa las entidades principales del sistema:

- Libros
- Usuarios
- Copias
- Préstamos
- Reseñas
- Categorías

📷 *(Aquí insertas la imagen del diagrama conceptual)*

------

## 🧱 Modelo Lógico

El modelo conceptual fue transformado en tablas relacionales con claves primarias (PK) y foráneas (FK).

Tablas principales:

- libros
- usuarios
- copias
- prestamos
- resenas
- categorias
- libro_categoria

📷 *(Aquí insertas la imagen del modelo lógico)*

------

## 🧠 Normalización (3FN)

La base de datos fue normalizada hasta la Tercera Forma Normal (3FN).

- Se eliminaron atributos multivaluados separando las categorías en una tabla independiente.
- Se dividieron los datos en múltiples tablas para evitar redundancia.
- Se eliminaron dependencias transitivas mediante la separación de entidades como categorías y reseñas.

Como resultado, la base de datos es consistente, organizada y sin duplicidad de información.

------

## 💻 Modelo Físico

Se implementó el modelo lógico mediante SQL, creando todas las tablas con sus respectivas claves primarias y foráneas.

📁 Archivo: `sql/script.sql`

------

## 🔍 Consultas SQL

Se desarrollaron consultas básicas para:

- Consultar libros disponibles
- Consultar préstamos de un usuario
- Consultar reseñas de un libro

📁 Archivo: `sql/consultas.sql`

------

## ⚙️ Restricciones Implementadas

- ISBN único en libros
- Email único en usuarios
- Relación obligatoria entre préstamos y usuarios
- Relación entre reseñas, usuarios y libros
- Control de disponibilidad mediante la tabla copias

------

## 📁 Estructura del Proyecto

```
/diagramas
   modelo_conceptual.png
   modelo_logico.png

/sql
   script.sql
   consultas.sql

README.md
```

------

## ✅ Conclusión

El sistema diseñado permite gestionar de forma eficiente la información de una biblioteca digital, solucionando problemas de organización, control de préstamos y almacenamiento de datos.

------
