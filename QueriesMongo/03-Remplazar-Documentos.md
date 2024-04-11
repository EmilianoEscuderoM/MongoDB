# Remplazar documentos


## Sustituir un documento completo

```
db.libros.replaceOne(
    {_id:2},
    {titulo:"De la tierra a la luna"},
    {autor:"Julio Berne"},
    {editorial:"Terra"},
    {precio:100}
)
```

## Borrar documentos

_Dos metodos_

1. deteleOne
2. deleteMany

**Eliminar todo el documento con un id = 2**

```
db.libros.deleteOne({_id:2})
```
**Eliminar todos los documentos donde la cantidad sea mayor a 150**

db.libros.deleteMany({cantidad : {$gt:150}})

# Expresiones regulares

**Seleccionar todos los documentos que contengan en el titulo una t**

```
db.libros.find({titulo:/t/})
```

**Seleccionar todos los documentos donde en el titulo contenga la palabra JSON**

```
db.libros.find({titulo:/JSON/})`
```

**Seleccionar todos los documentos en donde eltirulo terminen con la palabra tos**

```
db.libros.find({titulo:/tos$/})
```
**Seleccionar todos los documentos en donde el titulo termine en j**
```
db.libros.find({titulo:/j$/})
```

## Operador $regex

**Seleccionar todos los documentos que contenga las palabra para**

```
db.libros.find({titulo:{$regex:"para"}})
```

**Seleccionar todos los documentos donde el titulo contenga la palabra json que sea**

```
db.libros.find({titulo:{$regex:"json", $options: "i"}})
```

**Seleccionar todos los documentos de la coleccion libros donde el titulo contenga la palabra tos al final y que sea case sensitive**

```
db.libros.find({titulo:{$regex:/tos$/, $options: "i"}})
```

## Ver solo ciertas columnas
```
db.libros.find({},{titulo:1,_id:0})
```

**Seleccionar todos los documentos de la editorial Planeta pero mostrando solamente el titulo y la editorial**

```
db.libros.find({editorial:{$regex:"planeta", $options:"i"}},{editorial:1, titulo:1,_id:0})
```

## Operador exist

_Permite buscar la existencia de una columna_

```
db.libros.find({titulo:{$exists:true}})
```

## Operador type

```
db.libros.find({precio{$type:1}})

db.libros.find({precio{$type:"double"}})

db.libros.insertOne({titulo:"Java como programa", editorial:1})
```

## Tabla de tipo de datos en MongoDB

|Type|Number|Alias|
|-|-|-|
|Double|1|"double"|
| String |2| "string"|
| Object |3| "object" | 
| Array |4| "array" |
| Binary Data |5| "binData"|
| Undefined |6| "undefined" |
| ObjectId |7| "objectId" |
| Boolean |8| "bool" |
| Date| 9| "date"|
| Null |10| "null" |
| Regular expression|11| "regex"|
| DBPointer |12| "dbPointer"|
| JavaScript|13| "javascript"|
| Symbol | 14| "Symbol"|
| 32-bit integer|16| "int" |
| Timestamp|17| "timestamp" |
| 64-bit integer| 18| "long" |
| Decimal128 | 19| "decimal" |
| Min key |-1| "minKey" |
| Max key |127| "maxKey" |


## Operador #set

_Sirve para cambiar el valor de un campo dentro de la coleccion_

```
db.libros.updateOne({titulo:"Java como programa"},{$set:{titulo:"Como programar con Java"}})
```

**Actualizar el valor de la cantidad a 50 y el precio a 10 donde el id sea 9**

```
db.libros.updateOne({_id:9},{$set:{cantidad:50, precio:10}})
```

**Actualizar todos los documentos donde precio sea mayor a 10 por el precio a 150**

```
db.libros.updateMany({precio:{$gt:10}}, {$set:{precio:150}})
```

## Operador $sort

**Ordenar todos los documentos de forma ascendente por la editorial y mostrar solamente titulo, precio y editorial**

´´´
db.libros.find({}, {titulo:1,editorial:1,_id:0}).sort({editorial:1})
´´´