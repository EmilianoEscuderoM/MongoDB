# Insertar Documentos

_Inserta un solo documento_

```
db.Alumnos.insertOne(
    {
    Nombre: "Maximiliano"
    }
);
```
_Inserccion de un documento mas complejo con array_
```
db.Alumnos.insertOne(
    {
        Nombre: "Rosa",
        Edad: 22,
        Apellidos: "Cabeza de Vaca",
        Aficiones: 
        [
            "Paracaidismo", 
            "Lectura", 
            "Futbol"
        ]
    }
)
```

_Inserciones de documentos con documentos_

```
db.Alumnos.insertOne(
    {
        Nombre: "Raul",
        Edad: 67,
        CV: 
        {
            "Informatica" : "Bueno",
            "Marketing" : "Bajo",
            "Contabilidad" : "Malo"
        }
    }
)
```

_Insercion de documento con ID personalizado_

```
db.Alumnos.insertOne(
    {
        _id: 1,
        "Nombre" : "Arcadia"
    }
)
```

_Insertar multiples documentos_

```
db.Alumnos.insertMany( 
    [ 
        { _id: 2, 
        Nombre: "Diana" 
        }, 
        { _id: 3, 
        Nombre: "Flor", 
        Edad: 43 
        }, 
        { _id: 4, 
        Nombre: "Francisco", 
        Edad: 34, 
        Aficion: "El agua", 
        Desgracia: "Ex" 
        }
    ]
);
```

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