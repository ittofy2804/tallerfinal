Estructura de la Base de Datos en Firebase 

Este documento describe la estructura de la base de datos NoSQL en FireBase para el prototipo del proyecto final usando la base de datos Steam creada anteriormente en el semestre.
Su propósito es almacenar información a la base de datos Norelacional en FireBase.  
Mientras que MySQL maneja datos estructurados (tablas, relaciones y llaves foráneas), Firebase permite almacenar rapidamente
información, con un total de 10 registros para hacer una paginación sencilla, en el codigo de firePage.js esta limitado por 
lo que nos llegan 4 datos de los 10 registros guardados en FB que seria la page 1.

node routes/firePage.js (Resultado de paginación para game cambiando el nombre de la coleccion en firePage.js mostrado en consola)

1 {
  gameName: 'Shadow Rebellion',
  releaseDate: Timestamp { _seconds: 1557604145, _nanoseconds: 802000000 },
  price: 49,
  reviewScore: 8
}
10 {
  gameName: 'impactoGey',
  price: 10,
  releaseDate: Timestamp { _seconds: 1763581153, _nanoseconds: 262000000 },
}
2 {
  gameName: 'Fortnite',
  price: 2,
  releaseDate: Timestamp { _seconds: 1516356798, _nanoseconds: 935000000 },
  reviewScore: 9
}
3 {
  releaseDate: Timestamp { _seconds: 1466190825, _nanoseconds: 923000000 },
  reviewScore: 9,
  gameName: 'FIFA20',
  price: 5
}

node routes/firePage.js (Resultado de paginación para user cambiando el nombre de la coleccion en firePage.js mostrado en consola)

1 {
  username: 'alex_hunt',
  userPassword: 'hunter123',
  email: 'alex.hunt@mail.com',
  cellphone: '5551000001'
}
10 {
  cellphone: '3206453784',
  email: 'alenabu@mail.com',
  userPassword: 'ALEJF837',
  username: 'alenabu'
}
2 {
  cellphone: '3114636374',
  email: 'maria_p@mail.com',
  userPassword: 'auef234',
  username: 'maria_playz'
}
3 {
  cellphone: '5551000101',
  email: 'sofi.perez@example.com',
  userPassword: 'Sofi.2021!',
  username: 'sofiaperez'
}

---
Distribución de datos en FireBase: Los atributos para cada colección con su documento.
Colección: `user`

Contiene la información de los usuarios registrados.

| Campo          | Tipo de dato  | Descripción                    | Registro guardado      |
|----------------|---------------|--------------------------------|------------------------|
| `username`     | string        | Nombre de usuario único        | `"alex_hunt"`          |
| `userPassword` | string        | Contraseña del usuario         | `"hunter123"`          |
| `email`        | string        | Correo electrónico del usuario | `"alex.hunt@mail.com"` |
| `cellphone`    | string        | Número de teléfono del usuario | `"5551000001"`         |

---

Colección: `game`

Contiene la información de los juegos.

| Campo          | Tipo de dato | Descripción                           | Registro guardado                        |
|----------------|--------------|---------------------------------------|------------------------------------------|
| `gameName`     | string       | Nombre del juego                      | `"Shadow Rebellion"`                     |
| `price`        | number       | Precio del juego en dólares           | `49`                                     |
| `releaseDate`  | timestamp    | Fecha de lanzamiento del juego        | `11 de mayo de 2019, 2:49:05 p.m. UTC-5` |
| `reviewScore`  | number       | Calificación promedio de los usuarios | `8`                                      |

---

Colección: `library`

Relaciona usuarios con los juegos que han adquirido o jugado.

| Campo          | Tipo de dato | Descripción                             | Registro guardado                          |
|----------------|--------------|-----------------------------------------|--------------------------------------------|
| `username`     | string       | Usuario propietario del juego           | `"alex_hunt"`                              |
| `idGame`       | number       | Identificador del juego                 | `5`                                        |
| `hoursPlayed`  | number       | Horas jugadas                           | `120`                                      |
| `purchaseDate` | timestamp    | Fecha de compra o adición a la librería | `12 de marzo de 2023, 2:45:36 p.m. UTC-5`  |

---

Relaciones entre colecciones

`library.username` → hace referencia al `user.username`
`library.idGame` → corresponde al identificador del juego en la colección `game`

---



