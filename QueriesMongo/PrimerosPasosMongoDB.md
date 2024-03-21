# Primeros comandos en MongoDB

### Mostrar las base de datos

`show dbs;`
`show databases;`

### Crear una base de datos

*En mongodb para crear una base de datos debe contener por lo menos una coleccion*

`use NombreDeLaBaseDeDatos`

*Ejemplo:*
`use db1`

### Crear una colección

`db.createCollection("NombreDeLaColeccion")`

*Ejemplo:*

``db.createCollection("Alumnos")`

### Mostar las colecciones de la base de datos

*Ejemplo:*

`show collections`