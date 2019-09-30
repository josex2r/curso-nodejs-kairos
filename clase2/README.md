# Clase 2: Express

![Express_logo](../assets/express.png)

**Influencias / usos**

Otros frameworks similares:
- Zend (PHP)
- Django (Python)
- Sinatra (Ruby)

Uso:
- APIs
- SPA (Single Page Application)
- Tiempo real

**Pros**:
- Rutas
- Parámetros
- Formularios y subida de ficheros
- Cookies
- Sesiones
- Templates
- Middlewares

**Contras**:
- Base de datos / ORM
- Autenticación de usuarios
- Seguridad
- Migraciones
- Deployment
- Organización del código

**Migraciones**:
- [De Express 3.x a Express 4.x](http://expressjs.com/es/guide/migrating-4.html)
  - [Documentación de la 3.x (desuso)](http://expressjs.com/es/3x/api.html)
  - [Cambios](http://expressjs.com/es/guide/migrating-4.html)
  - [Nuevas funcionaldiades](https://github.com/expressjs/express/wiki/New-features-in-4.x?_ga=1.226364894.554285759.1461232316)
- [De Express 4.x a Express 5.x (hoy es Alpha)](http://expressjs.com/es/guide/migrating-5.html)
  - [Cambios Previstos](https://github.com/expressjs/express/pull/2237?_ga=1.29731835.554285759.1461232316)


**Instalación**

```bash
# Local
npm install express

# Global
npm install -g express

# Any version
npm install -g express@3.x
```

**Hello World!**

```javascript
const express= require('express');
const app = express();

app.get('/', (req, res) => res.send('Hello World!'));

app.listen(8080, () => console.log('Example app listening on port 8080'));
```

## Generador de Express

El generador de aplicaciones se utiliza para crear rápidamente un esqueleto de aplicación.

### Instalación

```bash
npm install express-generator -g

# Se puede generar el proyecto utilizando "npx"
npx express-generator <project_name>
```

Generar un proyecto (genera un directorio)

```bash
express <project_name>
```

Entramos en la carpeta e instalamos las dependencias

```bash
cd <nombre_proyecto> && npm install
```

### Estructura de un Proyecto (MVC)

```
├── app.js (Nuestra aplicación - módulo)
├── bin (Gestión de la aplicación)
│   └── www
├── package.json (Información y dependencias)
├── public (Nuestros estáticos)
│   ├── images
│   ├── javascripts
│   └── stylesheets
│       └── style.css
├── routes (Nuestros controladores)
│   ├── index.js
│   └── users.js
└── views (Nuestras vistas/plantillas)
    ├── error.jade
    ├── index.jade
    └── layout.jade
```

### Ejecutando la aplicación

```bash
# Window
set DEBUG=<nombre_proyecto>:* & npm start

# UNIX
DEBUG=<nombre_proyecto>:* npm start
```

> **Opcional**: [Volviendo el arranque al estilo Express 3.x](http://expressjs.com/es/guide/migrating-4.html#app-gen)

### Funcionalidades

- [express()](http://expressjs.com/es/4x/api.html#express)
- [Application](http://expressjs.com/es/4x/api.html#application)
- [Request](http://expressjs.com/es/4x/api.html#request)
- [Response](http://expressjs.com/es/4x/api.html#response)
- [Router](http://expressjs.com/es/4x/api.html#router)

#### El objeto `app`

**Mecánica: app.set()**
- Nos permite establecer la configuración de Express
- Podemos almacenar datos personalizados de manera global

Ej. Guardando la versión de la aplicación

```javascript
app.set('version', '1.5.0');
app.get('version'); // 1.5.0
```


```javascript
app.enable('dia_soleado'); // igual a -> app.set('dia_soleado', true);
app.enabled('dia_soleado'); // igual a -> app.get('dia_soleado') === true;
app.disabled('dia_soleado'); // igual a -> app.get('dia_soleado') === false;
```

Ej. Sobreescribiendo variables del framework:

```javascript
app.set('port', process.env.PORT || 3000);
```

> [Ver la lista de variables](https://expressjs.com/es/4x/api.html#app.settings.table)

Ej. Configuraciones según el entorno

 ```bash
 NODE_ENV=production node app.js
 ```

 ```javascript
 app.set('enable-some-functionality', process.env.NODE_ENV === 'production');
 ```

#### Motores de Plantillas

El objeto `locals` tanto de `app` como de cada vista es el responsable de pasar las variables al motor de plantillas.

**Variables locales a nivel de aplicación**:

```javascript
app.locals.title = 'My App';
app.locals.email = 'me@myapp.com';
```

**Variables locales a nivel de ruta**:

```javascript
app.get('/', (req, res) => {
  res.render('index', {
    title: 'Hey',
    message: 'Hello there!'
  });
});
```

**Cambiando el motor de renderizado a `pug`**:

```javascript
// npm install pug
const express = require('express');
const app = express();

app.set('view engine', 'pug');

app.listen(8080);
```

- [Comparativa de Motores de plantillas](https://developer.ibm.com/node/2014/11/11/compare-javascript-templates-jade-mustache-dust/)

#### Capturando peticiones HTTP

**Mecánica: app.all(), app.get(), app.post(), app.put(), app.delete(), app.route()**

```javascript
app[`METHOD`]('<route_name>', (request, response) => {});
```

Estructura:
- `app`: **Aplicación de express o router**
- `METHOD`: **[Metodo HTTP](https://www.wikiwand.com/es/Hypertext_Transfer_Protocol) de la Ruta**
  - Soportados: get, post, put, head, delete, options, trace, copy, lock, mkcol, move, purge, propfind, proppatch, unlock, report, mkactivity, checkout, merge, m-search, notify, subscribe, unsubscribe, patch, search y connect.
  - Para todas las rutas usamos *app.all()*
- `<route_name>`: **Ruta (url) donde aplica**
  - Cadenas de texto
  - Patrones en casenas de texto (Reducido a los subconjuntos: `?`, `+`, `*`, y `()`)
  - [Expresiones regulares](https://regex101.com/)
- `callback`: **La función que será llamada cuando se alcance la ruta con el método correctos**
  - Se pueden usar funciones
  - Se pueden usar arrays de funciones
  - Se pueden mezclar arrays y funciones
  - Argumentos:
    - Objeto `Request` de Node.js
    - Objeto `Response` de Node.js
    - `next()`: (Opcional) **Función que dispara el siguiente middleware**

Métodos HTTP: delimitando a un único método

```javascript
app.get('/', (req, res, next) => {
  res.send('Solo get como método me vale...');
});
```

Métodos HTTP: Otra forma de delimitar a un método

```javascript
app['m-search']('/', (req, res, next) => {
  res.send('Solo m-search como método me vale...');
});
```

Métodos HTTP: permitiendo todos los métodos

```javascript
app.all('/', (req, res, next) => {
  res.send('Cualquier método me vale...');
});
```

Rutas: Index (`http://localhost:8080`)

```javascript
app.get('/', (req, res, next) => {
  res.send('Esto es la Raiz');
});
```

Rutas: Básicas (`http://localhost:8080/hola`)

```javascript
app.get('/hola', (req, res, next) => {
  res.send('Esto es /hola');
});
```

Rutas: Capturando Parámetros (`http://localhost:8080/hola/Eduardo`, `http://localhost:8080/hola/Oscar`, ...)

```javascript
app.get('/hello/:nombre', (req, res) => {
    res.send('Hola ' + req.nombre + '!');
});
```

Rutas: Capturando varios parámetros (`http://localhost:8080/desde/Madrid/a/Malga`, `http://localhost:8080/desde/Madrid/a/NYC`)

```javascript
  app.get('/desde/:origen/a/:destino', (req, res, next) => {
    res.send('Quieres ir de ' + req.params.origen + ' a ' + req.params.destino);
  });
```
Rutas: Capturando varios parámetros y alguno determiando (`http://localhost:8080/mensaje/1/editar`, `http://localhost:8080/mensaje/500/borrar`, ...)

```javascript
  app.get('/mensaje/:id/:action(editar|borrar)', (req,res,next) => {
    res.send('Quieres ' + req.params.action + ' el mensaje numero ' + req.params.id);
  });
```

Rutas: Parámetros opcionales `http://localhost:8080/user/1/editar`, `http://localhost:8080/user/500/borrar`, ...

```javascript
app.get('/user/:id/:comando?', (req, res, next) => {
  if(req.params.comando){
    res.send("Tenemos algo! Quieres " + req.params.comando);
  } else {
    res.send("Nada de nada...");
  }
});
```

Rutas: Más parámetros opcionales (`http://localhost:8080/user/1.pdf`, `http://localhost:8080/user/500.zip`, ...)

```javascript
app.get('/user/:id.:formato?', (req, res, next) => {
  if(req.params.formato){
    res.send("["+req.params.formato+"] Extensión requerida... ");
  } else {
    res.send("Sin Extensión requerida");
  }
});
```

Rutas: Tipo fichero (`http://localhost:8080/hola.text`)

```javascript
app.get('/hola.text', (req, res) => {
  res.send('Hola');
});
```

Rutas: Patrones de serie (`http://localhost:8080/acd` o `http://localhost:8080/abcd*`)

```javascript
app.get('/ab?cd', (req, res) => {
  res.send('ab?cd');
});
```

Rutas: Patrones de serie (`http://localhost:8080/abcd`, `http://localhost:8080/abbbbbcd`, ...)

```javascript
app.get('/ab+cd', (req, res) => {
  res.send('ab+cd');
});
```

Rutas: Patrones de serie (`http://localhost:8080/abcd`, `http://localhost:8080/abAALGOOOcd`, ...)

```javascript
app.get('/ab*cd', (req, res) => {
  res.send('ab*cd');
});
```

Rutas: Patrones de serie (`http://localhost:8080/abe` o `http://localhost:8080/abcd*`)

```javascript
app.get('/a(bc)d', (req, res) => {
  res.send('a(bc)d');
});
```

Rutas: Expresiones regulares (`http://localhost:8080/mcfly`, `http://localhost:8080/dragonfly`, ...)

```javascript
app.get(/.*fly$/, (req, res) => {
  res.send('/.*fly$/');
});
```

**Definiendo diferentes métodos para la misma ruta con `app.route()`**:

```javascript
app.route('/pelicula')
  .get((req, res) => {
    res.send('todas las peliculas...');
  })
  .post((req, res) => {
    res.send('Añadir una pelicula...');
  })
```

**Handlers: Una única función**:

  ```javascript
  app.get('/example/a', (req, res) => {
    res.send('Hola desde A!');
  });
  ```

**Handlers: Varias funciones**:

```javascript
app.get('/example/b', (req, res) => {
  console.log('La respuesta se enviará a la siguiente función...');
  next();
}, (req, res) => {
  res.send('Hola desde B!');
});
```

Handlers: Arrays

```javascript
const cb0 = (req, res, next) => {
  console.log('CB0');
  next();
};

const cb1 = (req, res, next) => {
  console.log('CB1');
  next();
};

const cb2 = (req, res) => {
  res.send('Hola desde C!');
};

app.get('/example/c', [cb0, cb1, cb2]);
```

Handlers: Arrays y funciones

```javascript
const cb0 = (req, res, next) => {
  console.log('CB0');
  next();
};

const cb1 = (req, res, next) => {
  console.log('CB1');
  next();
};

app.get('/example/d', [cb0, cb1], (req, res, next) => {
  console.log('La respuesta se enviará a la siguiente función...');
  next();
}, (req, res) => {
  res.send('Hola desde D!');
});
```

#### Objeto `request`
- `req.ip`: **Almacena la IP desde donde se realizó la peticioón**
- `req.is`: **Que tipo de datos nos llegan desde la petición. Booleano**

```javascript
req.is('json');
req.is('application/*');
req.is('application/json');
```

- `req.params`: **Contenido de la ruta (http://localhost:8080/usuarios/:id)**
- `req.query`: **Contenido de la consulta de la URL (http://localhost:8080/peliculas?categoria=Ficcion&director=George+Lucas)**

```javascript
app.get('/peliculas', function(req,res,next){
  console.log(req.query.director) // George Lucas
  console.log(req.query.categoria) // Ficcion
});
```

- `req.body`: **Contenido dentro de la propia petición**

#### Objeto `response`

- [res.download()](http://expressjs.com/es/4x/api.html#res.download) *Solicita un archivo para descargarlo.*
- [res.end()](http://expressjs.com/es/4x/api.html#res.end) *Finaliza el proceso de respuesta.*
- [res.json()](http://expressjs.com/es/4x/api.html#res.json) *Envía una respuesta JSON.*
- [res.jsonp()](http://expressjs.com/es/4x/api.html#res.jsonp) *Envía una respuesta JSON con soporte JSONP.*
  - Valores por defecto ajustables en app.set()
    - *?callback=* valor por defecto en la petición
    - `res.jsonp({date: newDate()});`
- [res.redirect()](http://expressjs.com/es/4x/api.html#res.redirect) *Redirecciona una solicitud.*
- [res.render()](http://expressjs.com/es/4x/api.html#res.render) *Renderiza una plantilla a la que le pasa además datos (opcional)*
- [res.send()](http://expressjs.com/es/4x/api.html#res.send) *Envía una respuesta de varios tipos.*
  - Muy flexible
    - Código y contenido `res.send(404,'Oops...');`
    - Enviar un JSON `res.send({mensaje: "secreto"});`
    - Solo código (autocompleta el mensaje) `res.send(200);`
- [res.sendFile()](http://expressjs.com/es/4x/api.html#res.sendFile) *Envía un archivo para ser visualizado.*
- [res.sendStatus()](http://expressjs.com/es/4x/api.html#res.sendStatus) *Envía un archivo para ser descargado.*

#### Middlewares

Es una función que recibe 3 o 4 parámetros: `request`, `response`, `next`. Lo que hasta ahora llamábamos `handler`.

![Mw_schema](../assets/middleware.jpg)

Tipos:
- Middleware de nivel de aplicación
- Middleware de nivel de direccionador
- Middleware de manejo de errores
- Middleware incorporado
- Middleware de terceros

> Siempre que queramos continuar la ejecución y captura de la petición HTTP, es necesario invocar a `next()`.

**Mecánica: app.use()**:

```javascript
app.use((req, res, next) => {
  console.log("Petición en "+req.url+" con el método" + req.method);
  next();
});
```

```javascript
const express = require('express');
const app = express();

function chivato (req, res, next) {
  console.log(`Nueva petición en ${req.url} con el método ${req.method}`);
  next();
 };

app.use(chivato);

app.get('/', (req, res) => {
  res.send('Hola a todos!');
});

app.listen(3000);
```

**Middleware de nivel de aplicación**:

Global *Afecta a cualquier Ruta*

```javascript
const app = express();

app.use((req, res, next) => {
  console.log('Time:', Date.now());
  next();
});
```

Punto de Montaje *Afecta solo a una vía de acceso, en este caso /user/:id*

```javascript
const app = express();

app.get('/user/:id', (req, res, next) => {
  console.log('ID:', req.params.id);
  next();
}, (req, res, next) => {
  res.send('User Info');
});
```

#### Mapeado de parámetros en rutas

```javascript
app.param('user_id', (req, res, next, id) => {
  // Llamamos a una función que valida....
  someValidateUserFunction(id, (err, usuario) => {
    if (err) {
      next(err);
    } else if (user) {
      req.user = user
      next();
    } else {
      next(new Error('No user found with given ID'));
    }
  });
});

app.get('/user/:user_id', function (req, res, next) {
  // req.user contains the middleware value
  next()
})
```

#### Punto de Montaje (`Router`)

```javascript
const app = express();
const router = express.Router();
const USERS = [{
  id: 0,
  name: 'Jose'
}];

router.get('/user/:id', (req, res, next) => {
  res.send(USERS.find(({ id }) => id === req.params.id));
});

router.get('/users', (req, res, next) => {
  res.send(USERS);
});

app.use('api/v01', router);
```

#### Manejo de errores

```javascript
const bodyParser = require('body-parser');
const methodOverride = require('method-override');

function serverError(err, req, res, next) {
  if (req.xhr) {
    res.status(500).send({ error: 'Something failed!' });
  } else {
    res.status(500);
    res.render('error', { error: err });
  }
}

app.use(serverError);
```

#### Middlewares incorporados

Desde la versión 4.x Express no depende de [Connect](https://github.com/senchalabs/connect)
Solamente queda incorporado [express.static](https://github.com/expressjs/serve-static)

**Incluyendo archivos estáticos**:

```javascript
app.use(express.static('public'));
```

**Configurando la carpeta pública**:

```javascript
const options = {
  dotfiles: 'ignore',
  etag: false,
  extensions: ['htm', 'html'],
  index: false,
  maxAge: '1d',
  redirect: false,
  setHeaders(res, path, stat) {
    res.set('x-timestamp', Date.now());
  }
}

app.use(express.static('public', options));
```

**Usando múltiples directorios estáticos**:

```javascript
app.use(express.static('public'));
app.use(express.static('uploads'));
app.use(express.static('files'));
```

#### Middlewares útiles

Middleware oficial (No incorporado):
- [serve-favicon](https://github.com/expressjs/serve-favicon)
  - Sirve el favicon
- [Morgan](https://github.com/expressjs/morgan)
  - Logger para peticiones HTTP
- [body-parser](https://github.com/expressjs/body-parser)
  - Decodifica:
    - application/json
    - application/x-www-form-urlencoded
    - multipart/form-data
  - Crea el objeto req.body con los parámetros
  - Crea el objeto req.files con los ficheros que se han subido desde un formulario
- [basic-auth-connect](https://github.com/expressjs/basic-auth-connect)
  - Protección básica de las rutas usando usuario y contraseña
- [csurf](https://github.com/expressjs/csurf)
  - Crea *req.session._csrf*
  - Protección contra Cross-site request forgery
  - Usando tokens
- [cors](https://github.com/expressjs/cors)
  - Gestión de Cross Origin Resource Sharing (CORS)
- [compression](https://github.com/expressjs/compression)
  - [gzip](https://www.wikiwand.com/es/Gzip)
- [express-session](https://github.com/expressjs/session)
  - Simple gestor de sesiones
- [multer](https://github.com/expressjs/multer)
  - **Node.js middleware for handling `multipart/form-data`.**
- [cookie-session](https://github.com/expressjs/cookie-session)
  - **Simple cookie-based session middleware**
- [cookie-parser](https://github.com/expressjs/cookie-parser)
  - **cookie parsing middleware**
  - Crea req.cookies
- [cookie-session](https://github.com/expressjs/cookie-session)
  - Inicializa y parsea los datos de sesión del usuario
  - Utilizando cookies como almacenamiento
  - Algunas opciones avanzadas
- [serve-static](https://github.com/expressjs/serve-static)
  - **Serve static files**
  - ¡Muy útil! Se pone cerca del final
  - Cachea los ficheros
  - La variable global `__dirname` contiene el directorio donde reside el script en ejecución
- [vhost](https://github.com/expressjs/vhost)
  - Virtual Domain Hosting
- [restful-router](https://github.com/expressjs/restful-router)
  - **Simple RESTful url router.**
- [connect-markdown](https://github.com/expressjs/connect-markdown)
  - **Auto convert markdown to html for connect.**

> [La lista de Raynos](https://github.com/Raynos/http-framework)

**Habilitando CORS**:

```javascript
app.use(function(req, res, next) {
  res.header("Access-Control-Allow-Origin", "*");
  res.header('Access-Control-Allow-Methods', 'GET,PUT,POST,DELETE');
  res.header("Access-Control-Allow-Headers", "Origin, X-Requested-With, Content-Type, Accept");
  next();
});
```

**Baneando Navegadores (IE8 y anteriores)**:

```javascript
// ban.js
const banned = [ 'MSIE', 'Trident/6.0'];

module.exports = () => (req, res, next) =>{
  if (req.headers['user-agent'] !== undefined && req.headers['user-agent'].indexOf(banned) > -1) {
    res.end('Navegador no compatible');
  } else {
    next();
  }
};
```

**Redireccionando al usuario en caso de no estar autenticados**:

```javascript
module.exports = (req, res, next) => {
  if (req.params.usuario.logged){
    next();
  } else {
    res.redirect('/login');
  }
};
```

**[Ejemplos con Express](https://github.com/expressjs/express/tree/master/examples)**

### PUG (antes Jade)

![Jade_logo](../assets/jade.png)

**[Jade... ya no se llama jade. Ahora se llama PUG](https://github.com/pugjs/pug/issues/2184)**

![PUG_logo](../assets/pug.svg)

**Implementaciones en otros lenguajes**
- [php](https://github.com/kylekatarnls/jade-php)
- [scala](https://scalate.github.io/scalate/documentation/scaml-reference.html)
- [ruby](https://github.com/slim-template/slim)
- [python](https://github.com/SyrusAkbary/pyjade)
- [java](https://github.com/neuland/jade4j)


- **Entendiendo la mécanica**
  - index.jade:

    ```jade
    doctype html
    html(lang="en")
      head
        title= pageTitle
        script(type='text/javascript').
          if (foo) {
             bar(1 + 5)
          }
      body
        h1 Jade - node template engine
        #container.col
          if youAreUsingJade
            p You are amazing
          else
            p Get on it!
          p.
            Jade is a terse and simple
            templating language with a
            strong focus on performance
            and powerful features.
    ```

  - index.html:

    ```html
    <!DOCTYPE html>
    <html lang="en">
      <head>
        <title>Jade</title>
        <script type="text/javascript">
          if (foo) {
             bar(1 + 5)
          }
        </script>
      </head>
      <body>
        <h1>Jade - node template engine</h1>
        <div id="container" class="col">
          <p>You are amazing</p>
          <p>
            Jade is a terse and simple
            templating language with a
            strong focus on performance
            and powerful features.
          </p>
        </div>
      </body>
    </html>
    ```

- Bootstrap:
  - index.jade:

    ```jade
    doctype html
    html
      head
        title title
        include ./includes/styles.jade
      body
        .row
          .container
            .jumbotron
              h1 Hola, desde Bootstrap!
              p ¿Qué te parece?
              p
                a.btn.btn-primary.btn-lg(href='http://getbootstrap.com/', role='button') Aprende más!
        include ./includes/scripts.jade
    ```

  - includes/styles.jade

    ```jade
    //- includes/styles.jade
    // Bootstrap
    link(rel='stylesheet', href='//maxcdn.bootstrapcdn.com/bootstrap/3.3.5/css/bootstrap.min.css')
    ```

  - includes/scripts.jade

    ```jade
    //- includes/scripts.jade
    // Jquery
    script(src='//ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js')
    // Bootstrap
    script(src='//maxcdn.bootstrapcdn.com/bootstrap/3.3.5/js/bootstrap.min.js')
    ```

  - index.html

    ```html
    <!DOCTYPE html>
    <html>
      <head>
        <title>title</title>
        <!-- Bootstrap-->
        <link rel="stylesheet" href="//maxcdn.bootstrapcdn.com/bootstrap/3.3.5/css/bootstrap.min.css">
        </head>
      <body>
        <div class="row">
          <div class="container">
            <div class="jumbotron">
              <h1>Hello, desde Bootstrap!</h1>
              <p>¿Qué te parece?</p>
              <p>
                  <a href="http://getbootstrap.com/" role="button" class="btn btn-primary btn-lg">Aprende más!</a>
              </p>
            </div>
          </div>
        </div>
        <!-- Jquery-->
        <script src="//ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
        <!-- Bootstrap-->
        <script src="//maxcdn.bootstrapcdn.com/bootstrap/3.3.5/js/bootstrap.min.js"></script>
      </body>
    </html>
    ```

- [Pug - Github](https://github.com/pugjs/pug)
- [Pug - Getting Started](https://pugjs.org/api/getting-started.html)
- [Jade Syntax Documentation by example](http://naltatis.github.io/jade-syntax-docs/)


### Ejercicios

**1 -** Crearemos una aplicación utilizando Express para gestionar las películas que nos gustan.

**[Ver en el siguiente repositorio](https://github.com/josex2r/film-api)**
