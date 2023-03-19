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

+ ### **Con commondJS**

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

+ ### CommondJS

Creamos una carpeta *src* y dentro un archivo con el nombre de *server.js.*
Dentro de este archvo vamos a crear una class *Server* con un constructor y los métodos  listen() y  rutes()

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

Ahora usando la class *Server* que creamos en el archivo server.js instanciamos una nueva clase.
primero debemon importar en archivo y luego llamamos a los métodos listen() y routes()

```javascript
  javascript
  app.js

  const { Server } = require("./src/server.routes");

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
      this.app.get('/api', (req, res) => {
        res.status(201).json('Probando el servidor')
      })
      this.app.get('/api/users', (req, res) => {
        res.status(201).json('obtuviste un usuario')
      })
      this.app.delete('/api/delete', (req, res) => {
        res.status(201).json('Borraste un usuario')
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

  const { Server } = require("./src/server.routes");

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

### Nos vamos centrar en *users*

Dentro de la carpeta *routes* vamos a colocar todas nuestra rutas , en nustro caso vamos a crear la ruta usuarios.
Podemos crear el archivo *users.js* dentro de *rutes*, pero hay otra forma de nombrarlo que puede resultar mas semántico , por eso nostros vamos a nombrar las rutas siguiendo el siguiente patron nombre-ruta.routes.js, para serguir con el ejemplo vamos a crear dentro de rutes el archivo *users.routes.js*.

---

Hasta ahora llamamos a la libreria express y en nuesatro caso luego deberiamos llamar a su propiedad de enrutamiento Router

```javascript
  javascript
  users.routes.js

  const express = require ('express)

  express.Routes
  
```

Para evitar esto podemos desestructurar express y extraer el metodo Routes

```javascript
  javascript

  const { Routes} = require('express')
```

---

Una vez que tenemos el metodo *Routes* definimos una funcion en una constante llamada *rutes*(El nobre de la *const routes* es por convención), que es un función de enrutamiento en la que usamos el método Routes().

Ahora podemos acceder a todos los metodos de las rutas , ej : get , put, delete , etc.

+ ### **Con ES Modules**

---
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

[Volver al inicio](#nodejs)
