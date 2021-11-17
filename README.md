# Desarrollo de proyecto

## Creación de `package.json`

shell
$ npm init --yes

## Establecimiento de scripts en `package.json`

json
...
"scripts": {
"start": "node index.js",
"dev": "nodemon index.js"
}
...

## Construcción del archivo `index.js`

- Aplicamos arquitectura estándar:

javascript
// 1. IMPORTACIONES

// 2. MIDDLEWARES

// 3. RUTAS

// 4. SERVIDOR

## Instalación de librerías

- express
- dotenv
- hbs

shell
$ npm install express
$ npm install dotenv
$ npm install hbs

## Desarrollo de aplicación

- Las importaciones son el código externo e interno del proyecto.

- Recordar activar tus variables de entorno.

- Cuando levantes el servidor, recuerda utilizar `process.env.PORT` para vincularlo con el archivo `.env`

- Crea el archivo `.env` y pasa tu propiedad PORT.

javascript
// 1. IMPORTACIONES
const express = require("express")
const app = express()

require("dotenv").config()

// 2. MIDDLEWARES

// 3. RUTAS

// 4. SERVIDOR
app.listen(process.env.PORT, () => {
console.log(`Servidor activo en puerto ${process.env.PORT}`)
})

`.env`
PORT=3005

## Reconocer carpeta `public` y activar `hbs`

- Crear una carpeta `public`, con dos carpetas adicionales:

  - `images`
  - `stylesheets`
    - `index.css`

- Ejecutar este código. Tomando en cuenta la sección de `middlewares`:

javascript
// 1. IMPORTACIONES
const express = require("express")
const app = express()

require("dotenv").config()

// 2. MIDDLEWARES
app.use(express.static('public'))

app.set("views", \_\_dirname + "/views")
app.set("view engine", "hbs")

// 3. RUTAS

// 4. SERVIDOR
app.listen(process.env.PORT, () => {
console.log(`Servidor activo en puerto ${process.env.PORT}`)
})

## Activación de primera ruta

- Establecer la ruta con `app.get`
  - Primer parámetro. ¿Hacia dónde se dirige el usuario'
  - Segundo parámetro. La función que se ejecuta tan pronto el usuario toca esa ruta.
    - Dentro de esa función utilizamos `res.render` para establecer cuál vista usar.

javascript
// index.js

// 1. IMPORTACIONES
const express = require("express")
const app = express()

require("dotenv").config()

// 2. MIDDLEWARES
app.use(express.static('public'))

app.set("views", \_\_dirname + "/views")
app.set("view engine", "hbs")

// 3. RUTAS
app.get("/", (req, res) => {

    res.render("index")

})

// 4. SERVIDOR
app.listen(process.env.PORT, () => {
console.log(`Servidor activo en puerto ${process.env.PORT}`)
})
