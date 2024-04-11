# Operadores de comparación
| Operador | Descripcion |
| -- | -- |
| $eq | Igual |
| $gt | Mayor que |
| $gte | Mayor o igual |
| $in | Buscar un elemento en un arraay |
| $it | Menor que |
| $lte | Menor o igual |
| $ne | Todos los elementos que no sean iguales |
| $nin | Ninguno de los valores del array |

## Busquedas

_Selecciona todos los documentos de una coleccion_

```
db.libros.find()
db.libros.find({})
```

_Seleccionar todos los documentos de la coleccion libros donde la editorial sea biblio_

```
db.libros.find({editorial : "Biblio"})
```

_Seleccionar todos los documentos de la coleccion libro donde el precio sea igual a 25_

```
db.libros.find({precio : 25})
```

## Busquedas con operadores logicos

**Sintaxis**

```
{<columna>};
{<operador>:<valor>, ...}
```

_Seleccionar todos aquellos documentos de la coleccion libros donde el precio sea mayor a 25_

```
db.libros.find({precio : {$gt:25}})

```

_Seleccionar aquellos documentos de la coleccion libros donde el precio sea mayor o igual que 20_

```
db.libros.find({precio:{$gte:20}})
```

_Seleccionar aquellos documentos donde la editorial sea Biblio o Planeta_
```
db.libros.find({editorial:{$in:["Biblio","Planeta"]}})
```

## Recuperar una sola fila

_Seleccionar aquelos documentos que sean biblio o planeta, pero mostrando solamente el primer documento encontrado_

```
db.libros.findOne({editorial:{$in:["Biblio","Planeta"]}})
```

```
db1> db.libros.findOne({})
```

# Operadores lógicos

|Operador|Descripción|
|--|--|
|$and|Operador And: Devuelve los documentos que cumplen todas las condiciones|
|$or|Operador Or: Devuelve los documentos que cumplen alguna condición|
|$not|Invierte el resultado de una condición|
|$nor|Devuelve los documentos que no cumplen lascondiciones|
|$exist|Devuelve los documentos que tengan un campo concreto|
|$type|Selecciona los documentos si un campo pertenece a un tipo especifico|

## Operador AND

```
db.coleccion.find({condicion1, condicion2})
```

```
db.coleccion.find({$and:[{condicion1},{condicion2}]})
```
_Seleccionar todos aquellos libros que valgan mas de 25 y cuya cantidad sea inferior a 15_

```
db.libros.find({$and:[{precio:{$gte:25}},{cantidad:{$lt:15}}]})
```

## Operador OR

**Sintaxis**

_Seleccionar todos aquellos libros que valgan mas de 25 ó cuya cantidad sea inferior a 15_

```
db.libros.find({$or:[{precio:{$gte:25}},{cantidad:{$lt:15}}]})
```

## OR y AND combinadas

_Seleccionar los documentos de la editorial biblio con precio mayor a 40 o libros de la editorial planeta con precio mayor a 30_
