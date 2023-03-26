# **node.js**

Node.js es un entorno de ejecución de JavaScript orientado a eventos asincronos .
Es multiplataforma, de código abierto, con E/S de datos y corre con el  motor V8 de Google.

---

Para la ralización de nuestros proyectos vamos a utilizar [Postman](#postman) y [Nodemon](#nodemon).
Podes encontrar un pequeño resumen haciendo click en la enlace o al final de este documento.

---

+ ## **Iniciar proyecto en node.js**

Para iniciar un proyecto en node.js corremos el comando node init en la consola, debemos estar ubicados en la carpeta destinada al proyecto.
Esto nos permitara personalizar algunas características.

```js
  consola

Nestor@DESKTOP-2023 EQUIPO ~/carpeta-del-proyecto 
$ npm init
```

Si queremos instalar el proyecto de manera rápida podemos correr el comando node init -y.

```js
  consola

Nestor@DESKTOP-2023 EQUIPO ~/carpeta-del-proyecto 
$ npm init -y
```

---

+ ## **Correr nuestra aplicacion en consola**

Ahora estamos listos para correr js en la consola.
Para eso ejecutamos en comando node nombre-archivo.js.

```js
  consola

Nestor@DESKTOP-2023 EQUIPO ~/carpeta-del-proyecto 
$ node app.js
```

En el archivo package.json que se instala con node tenemos los scripts donde podemos agregar scripts personalizados. Por ejemplo para correr nuestro programa
en el script escribimos: "start": "node app.js".

```json
  package.json

  {
    "name": "clase-01",
    "version": "0.0.1",
    "description": "nuevo servidor de la clase 1 de back",
    "main": "index.js",
    "scripts": {
      "test": "echo \"Error: no test specified\" && exit 1",
      "start": "node app.js",
    },
    "author": "Nestor Labiuk",
    "license": "MIT",
    "dependencies": {
      "express": "^4.18.2",
      "nodemon": "^2.0.21"
    }
  }

```

Ahora podemos correr en consola:

```js
  consola

Nestor@DESKTOP-2023 EQUIPO ~/carpeta-del-proyecto 
$ npm run start
```

En el caso de start no hace falta escribir run ,porque es el comando por defecto para inicializar nuestra aplicación, pero si en el resto de los script

```js
  consola

Nestor@DESKTOP-2023 EQUIPO ~/carpeta-del-proyecto 
$ npm start
```

---

+ ## **Crear un servidor web**

Ahora que tenemos instalado Node.js, podemos crear nuestro primer servidor web.
Creamos un archivo app.js con el siguiente contenido:

```javascript
  javascript

const http = require('http');

const hostname = '127.0.0.1';
const port = 3000;

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
  res.end('Hola Mundo');
});

server.listen(port, hostname, () => {
  console.log(`El servidor se está ejecutando en http://${hostname}:${port}/`);
});
```

Ahora podemos correr nuestro servidor usando "npm start".
Si abrimos un ventana del navegador en "http://localhost:3000" veremos el mensaje "Hola Mundo".

---

Ver documentación oficial en :

+ Ingles "https://nodejs.org/en/about"
+ Español "https://nodejs.org/es/about"

---
---

## **Expressjs o Express**

+ Es un framework flexible basado en Node.js , que proporciona un conjunto de herramientas que facilita en trabajo para crear aplicaciones web y aplicaciones movil.

+ Contiene numerosas utilidades HTTP y middleware´s.

Express nos permite crear un servidor web de manera mucha mas secilla que la que vimos en el punto enterior, con node.js puro.

---

+ ## **Instalar Express**

En la consola ejecutamos el siguiente comando:

```js
  consola

Nestor@DESKTOP-2023 EQUIPO ~/carpeta-del-proyecto 
$ npm install express
```

---

+ ## **Crear servidor con express**

Hay dos maneras crear un servidor web con express, la forma antigua es con commond.js y la mas moderna es con ES Modules.

---
---

## 1. **CommondJS**

Primero vamos a trabajar con commonjs.

Levantamos un servidor:

```javascript
  javascript
  app.js

  const express = require('express')

  const app = express()

  app.get('/', (req, res) => {
    res.send('Hola Mundo')
  })

  app.listen(8080, () => {
    console.log(`El servisor esta corriendo en el puerto ${8080}`)
  })

```

---

+ ## **Métodos de ruta**

Un método de ruta se deriva de uno de los métodos HTTP y se adjunta a una instancia de la clase express.

El siguiente código es un ejemplo de las rutas que se definen para los métodos GET ,POST ,PUT, PATCH Y DELETE a la raíz de la aplicación.

En este ejemplo vamos a utilizar el metodo "status" en el cual le pasamos el estado de la petición, por defecto nos devuelve un estatus(200).

Tambien vamos a pasar la respuesta en formato json.

```javascript
  javascript
  app.js

  app.get('/', (req, res) => {
    res.status(201).json('GET request');
  });

  app.post('/', (req, res) => {
    res.status(201).json('POST request');
  });

  app.put('/api', (req, res) => {
    res.status(201).json('PUT request')
  })

  app.patch('/api', (req, res) => {
    res.status(201).json('PATCH request')
  })

  app.delete('/api', (req, res) => {
    res.status(201).json('DELETE request')
  })
  
```

---

+ ### **Códigos de estado de respuesta HTTP**

Los códigos de estado de respuesta HTTP indican si se ha completado satisfactoriamente una solicitud HTTP específica. Las respuestas se agrupan en cinco clases:

1. Respuestas informativas (100–199),
2. Respuestas satisfactorias (200–299),
3. Redirecciones (300–399),
4. Errores de los clientes (400–499),
5. Errores de los servidores (500–599).

Para ver la descripción completa visita el siguiente enlace:
"https://developer.mozilla.org/es/docs/Web/HTTP/Status"

---
---

## **Refactorizar parte 1**

Ahora que tenemos las herramientas básicas podemos comenzar a refactorizar el código

---

+ ### **Creando nuestro servidor**

Creamos una carpeta *src* y dentro un archivo con el nombre de *server.js.*
Dentro de este archivo vamos a crear una class *Server* con su constructor y los métodos  listen() y  rutes()

Como estamos usando commond.js para exportar devemos usar el método *module.exports.*

```javascript
  javascript
  server.js

  const express = require('express')

  class Server {
    
    constructor(){
      this.app = express()
    }

    routes() {
      this.app.get('/api', (req, res) => {
        res.json('Probando el servidor')
      })
    }
  
    listen() {
      this.app.listen(8080, () => {
        console.log('El servidor esta corriendo en la puerto 8080')
      })
    }
  }

  module.exports = {
    Server
  }
```

---

+ ### **Instanciar un nuevo servidor**

Ahora usando la class *Server* que creamos en el archivo server.js instanciamos una nueva clase en nuestro archivo *app.js*
Primero debemos importar *server.js* y luego llamamos a los métodos listen() y routes()

```javascript
  javascript
  app.js

  const { Server } = require("./src/server");

  const server = new Server

  server.routes()
  server.listen()

```

---

Ahora agregamos mas rutas a nuestra class *Server* y en el constructor agregamos *this.routes()* de esta manera no tenemos que llamar al las rutas en nuestro app.js

```javascript
  javascript
  server.js

  const express = require('express')

  class Server {
  
    constructor(){
      this.app = express()

      this.routes()
    }

    routes() {
      this.app.get('/api/users', (req, res) => {
        res.status(201).json('Obtuviste los usuarios')
      })
      this.app.post('/api/users', (req, res) => {
        res.status(201).json('Creaste un usuario')
      })
    }

    listen() {
      this.app.listen(8080, () => {
        console.log('Servidor levantado en la puerto 8080')
      })
    }
  }

  module.exports = {
    Server
  }

```

```javascript
  javascript
  app.js

  const { Server } = require("./src/server");

  const server = new Server

  server.listen()

```

---

## **Refactorizar parte 2**

Podemos mejorar nuestro código separandolo en distintos archivos y carpetas

---

Se puede ordenar de distintas maneras. Nosotros vamos a crear una carpeta *routes* , una carpeta *controllers* y si es necesario una carpeta llamada *models*.
Algunos desarrolladores colocan el *server.js* dentro de la carpeta de *models*, pero en nuestro caso la colocamos solo dentro de la carpeta *src*.

---

Ya que la gran mayoria de las aplicaciones tienen un apartado usuarios:

+ ### Nos vamos centrar en *users*

Dentro de la carpeta *routes* vamos a colocar todas nuestra rutas , en nuestro caso vamos a crear la ruta usuarios.
Podemos crear el archivo *users.js* dentro de *rutes*, pero hay otra forma de nombrarlo que puede resultar mas semántico , por eso nostros vamos a nombrar las rutas siguiendo el siguiente patron nombre-ruta.routes.js, para serguir con el ejemplo vamos a crear dentro de rutes el archivo *users.routes.js*.

---

Ahora vamos a comenzar a crear las rutas y las vamos a separar del *server.js*.

Para eso vamos a usar el archvivo *users.routes.js*

Podriamos llamar a la libreria express y luego  a su propiedad de enrutamiento Router

```javascript
  javascript
  users.routes.js

  const express = require ('express)

  express.Routes
  
```

---

Ya que solo vamos a necesitar el enrutamiento vamos a desestructurar express y extraer el método Routes

```javascript
  javascript
  users.routes.js

  const { Routes} = require('express')
```

---

Una vez que tenemos el metodo *Routes* definimos una funcion en una constante llamada *rutes*(El nobre de la *const routes* es por convención), que es un función de enrutamiento en la que usamos el método Routes().

```javascript
  javascript
  users.routes.js

  const { Routes } = require('express')

  const router = Routes()
  
```

---

Con router podemos acceder a todos los metodos de las rutas , ej : get , put, delete , etc.

Ahora podemos crear las rutas que necesitamos en *users.rutes.js* y las exportamos a *server.js* , donde  vamos a usar la propiedad *use* a la que le pasamos los como parametros la ruta en la que estamos y a la que queremos dirigirnos.

```javascript
  javascript
  users.routes.js
  
  const { Router} = require('express')

  const router = Router()

  router.get('/users', (req, res) => {
    res.json('Obtuviste los usuarios')
  })

  router.post('/users', (req, res) => {
    res.json('creaste un usuario')
  })

  module.exports = {
    router
  }
```

```javascript
  javascript
  server.js

  const express = require('express')
  const { router} = require('./routes/users.routes',)

  class Server {

    constructor() {
      this.app = express()
      this.routes()
    }

    routes() {
      this.app.use('/api', router)
    }

    listen() {
      this.app.listen(8080, () => {
        console.log('Servidor levantado en la puerto 8080')
      })
    }
  }

  module.exports = {
    Server
  }
```

---

## **Refactorizar parte 3**

Para seguir mejorando nuestro código ahora vamos a usar los controladores.

Estos son archivos donde vamos a colocar la funciones de callback que usamos en las rutas y luego las llamaremos por referencia.

Siguiendo con nuestro ejemplo de *usuarios* vamos a crear un archivo llamado users.controller.js dentro de la carpeta controllers que habiamos creado anteriormente. [ver](#refactorizar-parte-2)
También agregamos una neva ruta para editar usuarios

---

### Nuestro código quedaria estructurado de la siguiente manera

+ En la carpeta Controllers dentro de src:

```javascript
  javascript
  users.cotrollers.js

  const getUsers = (req, res) => {
  res.json('Obtuviste los usuarios')
  }
  const createUsers = (req, res) => {
    res.json('Creaste un usurio')
  }
  const editUsers = (req, res) => {
    res.json('Editaste un usuario')
  }

  module.exports = {
    getUsers,
    createUsers,
    editUsers
  }

```

+ El la carpeta routes dentro de src:

```javascript
  javascript
  users.routes.js

  const { Router } = require('express')
  const { getUsers, createUsers, editUsers } = require('../controllers/users.controllers')

  const router = Router()

  router.get('/users', getUsers)
  router.post('/users', createUsers)
  router.put('/users', editUsers)

  module.exports = {
    router
  }
  
```

+ En la carpeta src:

```javascript
  javascript
  server.js

  const express = require('express')
  const { router} = require('./routes/users.routes',)
  const { routerProducts } = require('./routes/products.routes')

  class Server {

    constructor() {
      this.app = express()
      this.routes()
    }

    routes() {
      this.app.use('/api', router)
      this.app.use('/api', routerProducts)
    }

    listen() {
      this.app.listen(8080, () => {
        console.log('Servidor levantado en la puerto 8080')
      })
    }
  }

  module.exports = {
    Server
  }
```

+ En la carpeta raiz:

```javascript
  javascript
  app.js

  const { Server } = require("./src/server");

  const server = new Server

  server.listen()
```

---
---

## 2. **ES Modules (parte 1)**

Esta es la forma mas moderna de trabajar. Se usan las palabras clave *import* y *export*.

En las inportaciones tenemos que especificar la extención del archivo.

---

### Comenzaremos un nuevo proyecto y haremos algunas modificaciones en la instalación

---

Creamos una nueva carpeta y dentro colocamos un archivo *app.js* y una carpeta llamada *src*, dentro de esta colocamos el archivo *server.js*.
Podemos ver la estructura final de carpetas [AQUI](#carpetas)

---

+ instalamos node:

```js
  consola

Nestor@DESKTOP-2023 EQUIPO ~/carpeta-del-proyecto 
$ npm init -y
```

+ Instalamos express:

```js
  consola

Nestor@DESKTOP-2023 EQUIPO ~/carpeta-del-proyecto 
$ npm install express
```

+ Instalamos nodemon como dependencia de desrrollo

```js
  consola

Nestor@DESKTOP-2023 EQUIPO ~/carpeta-del-proyecto 
$ npm install nodemon --save-dev
```

---

Para poder trabajar con ES Modules tenemos que hacer una configuración en el package.json: agregamos *"type": "modules"*

Tambien agragamos  los escripts para levantar el servidor
*"start":"node app.js"* y *"dev":"nodemon app.js"*

```json
  package.json

  {
    "name": "back-clase-02",
    "version": "1.0.0",
    "description": "Práctica de back usando EC Modules",
    "main": "app.js",
    "type":"module",
    "scripts": {
      "test": "echo \"Error: no test specified\" && exit 1",
      "start":"node app.js",
      "dev":"nodemon app.js"
    },
    "keywords": [],
    "author": "Néstor Labiuk",
    "license": "MIT",
    "dependencies": {
      "express": "^4.18.2"
    },
    "devDependencies": {
      "nodemon": "^2.0.21"
    }
  }
```

---

En la carpeta raiz agregamos los archivos *.env*  y *.gitignore*.

*.env* de envaironment , en este arvhivo se colocan las variables de entorno de nuestro proyecto aqui vamos a colocar el puerto : *PORT=8080*.Tambien agregaremos las rutas para conectarnos con nuestra BBDD.
*.gitignore* aqui se colocan las carpetas y archivos que no queremos que se suban a nuestro repo. Aqui vamos a colocar por *.env* y *node_modules* entre otros.

---

En nuestra carpeta *routes* vamos a colocar los distintos archivos con las distintas rutas , como digimos anteriormente creamos una varible *const router* para acceder al método Router(), en esa varible vamos a colocar todas las rutas de ese archivo. Si nombramos en todos los archivos al método Router() con la misma variable,*const = routes* cuando la importemos al archivo *server.js* vamos a tener un conflicto de nombre de variable. Tenemos dos alternativas, la primera es nombrar a la variable que contenga al 0 método Router() de manera distinta (Ej: en user *const usersRoutes = Router(), en products productsRoutes = Router()*), la otra forma es aprovecharnos de la propiedad que tenemos al exportamos por default que nos permite nombrarla como nosotros querramos al importarla.
Nosotros vamos a utizar este último metodo.

Cuando tenemos muchas rutas se usa un archivo tipo barril que normanlmente se nombra como index.js y se coloca dentro de la carpeta routes.
Este archivo lo que hace es *recibir y exportar las rutas*.

---

```javascript
  javascript
  app.js
  
  import { Server } from './src/server.js'

  const server = new Server()

  server.listen()

```

---

```javascript
  javascript
  server.js
  
  import express from 'express'
  import { usersRoutes } from './routes/index.js'

  export class Server {
    constructor () {
      this.app = express()
      this.routes()
    }

    routes () {
      this.app.use('/api/users', usersRoutes)
    }

    listen () {
      this.app.listen(8080, () => {
        console.log('Servisor corriendo en el puerto 8080')
      })
    }
  }

```

---

```javascript
  javascript
  index.js

  export { default as userRoutes } from './users.routes.js'

```

En el archivo users.routes.js tenemos dos métodos post para diferenciarlos al mas específico le agregamos *:id* para poder llamarlo con ese parámetro.

```javascript
  javascript
  users.routes.js
  
  import { Router } from 'express'
  import { getUsers, getUser, createUser, editUser, deleteUser } from '.././controllers/users.controllers.js'
  const router = Router()

  router.get('/', getUsers)
  router.get('/:id', getUser)
  router.post('/', createUser)
  router.put('/', editUser)
  router.delete('/', deleteUser)

  export default router

```

En users.controllers.js pasamos por parámetro el id para poder personalizar el mensaje.

```javascript
  javascript
  users.controllers.js
  
  export const getUsers = (req, res) => {
  res.json('Obtuviste los usuarios')
  }

  export const getUser = (req, res) => {
    const { id } = req.params
    res.json(`Obtuviste un usuario con el ${id}`)
  }

  export const createUser = (req, res) => {
    res.json('Creaste un usuario')
  }

  export const editUser = (req, res) => {
    res.json('Editaste un usuario')
  }

  export const deleteUser = (req, res) => {
    res.json('Borraste un usuario')
  }

```

---

Hasta aca hicimos nuentra aplicación de back usando ES Modules y le agregamos algunas funcionalidades.

---

---

## **ES Modules (parte 2)**

---

## **Postman**

[Volver al inicio](#nodejs)

Postman es una plataforma API para que los desarrolladores diseñen, construyan, prueben e iteren sus APIs.

Postman permite y hace más sencilla la creación y el uso de APIs. Esta herramienta es muy útil para programar porque da la posibilidad hacer pruebas y comprobar el correcto funcionamiento de los proyectos que realizan los desarrolladores web.

Instala la aplicación de escritorio de postman desde el siguiente enlace
"https://www.postman.com/downloads/"

---

---

## **Nodemon**

[Volver al inicio](#nodejs)

Nodemon es una utilidad que monitoriza cualquier cambios en su codigo y reinicia automáticamente su servidor. Perfecto para el desarrollo.

+ ## **Características**

  + Reinicio automático de la aplicación.
  + Detecta la extensión de archivo predeterminada para monitorear.
  + Ignorar archivos o directorios específicos.
  + Ver directorios específicos.
  + Funciona con aplicaciones de servidor o utilidades de ejecución única y REPL.
  + Código abierto y disponible en github.
  
---

+ ### **Intalacion**

```js
  consola

Nestor@DESKTOP-2023 EQUIPO ~/carpeta-del-proyecto 
$ npm install nodemon
```

---

+ ### **correr nodemon**

```js
  consola

Nestor@DESKTOP-2023 EQUIPO ~/carpeta-del-proyecto 
$ nodemon app.js
```

Este comando en ocaciones no funciona.
Entonces en nuestro archivo package.json creamos un nuevo escript:

"dev": "nodemon app.js"

```json
  package.json

  {
    "name": "clase-01",
    "version": "0.0.1",
    "description": "nuevo servidor de la clase 1 de back",
    "main": "index.js",
    "scripts": {
      "test": "echo \"Error: no test specified\" && exit 1",
      "start": "node app.js",
      "dev": "nodemon app.js"
    },
    "author": "Nestor Labiuk",
    "license": "MIT",
    "dependencies": {
      "express": "^4.18.2",
      "nodemon": "^2.0.21"
    }
  }

```

Ahora podemos ejecutar

```js
  consola

Nestor@DESKTOP-2023 EQUIPO ~/carpeta-del-proyecto 
$ npm run dev
```

---

## Carpetas

+ nombre-carpeta
  + dist
  + node_module
  + src
    + controllers
      + users.controllers.js
      + products.controllers.js
    + routes
      + users.routes.js
      + products.routes.js
      + index.js
    + model
    + middlewares
    + db
    + serer.js
  + .env
  + .gitignore
    + .env
    + node_module
    + dist/
  + app.js
  + package-lock.json
  + package.json
  + readme-md

---

[Volver al inicio](#nodejs)
