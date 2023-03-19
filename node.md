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

## **Métodos de ruta**

Un método de ruta se deriva de uno de los métodos HTTP y se adjunta a una instancia de la clase express.

El siguiente código es un ejemplo de las rutas que se definen para los métodos GET ,POST ,PUT, PATCH Y DELETE a la raíz de la aplicación.

En este ejemplo vamos a utilizar el metodo "status" en el cual le pasamos el estado de la petición, por defecto nos devuelve un estatus(200).

Tambien vamos a pasar la respuesta en formato json.

```javascript
  javascript

  // GET method route
  app.get('/', (req, res) => {
    res.status(201).json('GET request');
  });

  // POST method route
  app.post('/', (req, res) => {
    res.status(201).json('POST request');
  });

  // PUT method route
  app.put('/api', (req, res) => {
    res.status(201).json('PUT request')
  })

  // PATCH method route
  app.patch('/api', (req, res) => {
    res.status(201).json('PATCH request')
  })

  // DELETE method route
  app.delete('/api', (req, res) => {
    res.status(201).json('DELETE request')
  })
  
```

---

+ ### **Códigos de estado de respuesta HTTP**

 "https://developer.mozilla.org/es/docs/Web/HTTP/Status"

---

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

Ahora podemos ejecutar

```js
  consola

Nestor@DESKTOP-2023 EQUIPO ~/carpeta-del-proyecto 
$ npm run dev
```

---

[Volver al inicio](#nodejs)
