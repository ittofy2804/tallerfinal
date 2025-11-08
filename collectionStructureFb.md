# Estructura de la Base de Datos en Firebase

Este documento describe la estructura de la base de datos NoSQL utilizada en el proyecto.  
La base se implementa en **Firebase Firestore** y cuenta con tres colecciones principales: `user`, `game` y `library`.  
Cada una almacena datos de usuarios, juegos y las relaciones entre ellos (biblioteca de juegos adquiridos o jugados).

---
node routes/firePage.js (Resultado de paginación para user cambiando el nombre de la coleccion en firePage.js mostrado en consola)

1 {
  cellphone: 3505498870,
  email: 'ittofy28@mail.com',
  userPassword: 'ittofyyyy',
  username: 'ittofy28'
}
10 {
  cellphone: 3138097232,
  mail: 'makiiiii@mail.com',
  UserPassword: 'soymaki',
  userName: 'makistun\n'
}
2 {
  cellphone: 3212235647,
  email: 'electrifire@mail.com',
  userPassword: 'caribeelector\n',
  username: 'electrifire'
}
3 {
  cellphone: 3138097535,
  email: 'juanchopizza@mail.com',
  userPassword: 'pizzaaajuancho',
  username: 'juanchopizza'
}

## Colección: user

Guarda la información de los usuarios registrados dentro de la aplicación.

| Campo | Tipo de dato | Descripción | Ejemplo |
|--------|---------------|--------------|----------|
| `username` | string | Nombre de usuario único | `"it_tofy28"` |
| `userPassword` | string | Contraseña del usuario (no cifrada en este caso) | `"ittofyyy"` |
| `email` | string | Correo electrónico del usuario | `"ittofy28@mail.com"` |
| `cellphone` | number | Número de teléfono o contacto | `3505498870` |

---

## Colección: game

Contiene la información de los juegos disponibles en la base de datos.

| Campo | Tipo de dato | Descripción | Ejemplo |
|--------|--------------|--------------|----------|
| `gameName` | string | Nombre del juego | `"GTA8"` |
| `price` | number | Precio del juego en la moneda definida (ej. dólares o pesos) | `200` |
| `releaseDate` | timestamp | Fecha de lanzamiento del juego | `15 de febrero de 2017, 5:07:00 p.m. UTC-5` |
| `reviewScore` | number | Calificación o puntuación del juego | `6` |

---

## Colección: library

Relaciona a los usuarios con los juegos que poseen o han jugado.

| Campo | Tipo de dato | Descripción | Ejemplo |
|--------|--------------|--------------|----------|
| `username` | string | Usuario propietario del juego | `"ittofy28"` |
| `idGame` | number | Identificador del juego (coincide con el ID del documento en la colección `game`) | `2` |
| `hoursPlayed` | number | Horas jugadas por el usuario | `120` |
| `purchaseDate` | timestamp | Fecha en la que el usuario adquirió o añadió el juego a su biblioteca | `13 de octubre de 2025, 2:02:30 p.m. UTC-5` |

---

## Relaciones entre colecciones

- `library.username` → hace referencia al campo `user.username`  
- `library.idGame` → corresponde al identificador del juego en la colección `game`

---

## Descripción general

Esta estructura permite manejar de forma sencilla la relación **usuario ↔ juegos**, facilitando consultas como:

- Listar los juegos que posee un usuario.  
- Mostrar las horas jugadas por cada usuario.  
- Consultar información del juego desde la biblioteca (`library`) usando el `idGame`.
---

Relaciones entre colecciones

`library.username` → hace referencia al `user.username`
`library.idGame` → corresponde al identificador del juego en la colección `game`

---



