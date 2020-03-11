# Cursod e Creacion de Router para Single Page App con JavaScript <!-- omit in toc -->

## Tabla de Contenido

- [Tabla de Contenido](#tabla-de-contenido)
- [La logica detras del enrutador](#la-logica-detras-del-enrutador)
- [Estructura de la aplicacion](#estructura-de-la-aplicacion)
- [Desgloce del Proyecto](#desgloce-del-proyecto)
- [Implementando routing del lado del cliente](#implementando-routing-del-lado-del-cliente)
- [Creamos el HTML base](#creamos-el-html-base)
- [Creamos nuestras Rutas](#creamos-nuestras-rutas)
- [Creacion del Router](#creacion-del-router)
- [Creamos la function _loadInitialRoutes](#creamos-la-function-loadinitialroutes)
- [Creamos nuestra funcion para hacer match de la URL](#creamos-nuestra-funcion-para-hacer-match-de-la-url)
- [Creamos la funcion para cargar la ruta](#creamos-la-funcion-para-cargar-la-ruta)
- [Agregamos nuestrp Index.js](#agregamos-nuestrp-indexjs)
- [Router terminado](#router-terminado)
- [Comentarios](#comentarios)

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## La logica detras del enrutador

- Cargar Ruta: identificar en donde nos encontramos en el sitio.
- Comparar URL con la Ruta: a url a la que nos queremos mover se debe comparar con las rutas que tenemos.
- Actualizar la URL en la barra de navegacion: para esto utilizaremos el metodo de HTML pushState.
- Actualizar el DOM: para esto vamos a utilizar innerHTML.

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Estructura de la aplicacion

- HTML basico que vamos a actualizar con el contenido.
- Index.js que tiene la logica del contenido.
- Routes.js que tiene las rutas.
- Router.js que tiene la logica del enrutador.

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Desgloce del Proyecto

Cosas que se esperan del comportamiento de una SPA. 

- Poder navegar utilizando las flechas del navegador.
- Ver cambios en la url.
- No tener que cargar la pagina completa cada vez que se realiza una accion.

Para esto nos ayudaremos del Browser API, utilizando el metodo pushState del elemento history del objeto window para poder manejar nuestra navegacion en el stack.

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Implementando routing del lado del cliente

La sintaxis para hacer actualizaciones de la ruta es:
```js
window.history.pushState({data: 'Movimiento'}, 'Title', '/path');
```

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Creamos el HTML base

```html
<!DOCTYPE html>
<html lang="en">

<head>
  <title>Document</title>
</head>

<body>

  <header>
    <ul>
      <li><button onclick="router.loadRoute('')">Inicio</button></li>
      <li><button onclick="router.loadRoute('about')">Acerca de mi</button></li>
      <li><button onclick="router.loadRoute('contact')">Contacto</button></li>
    </ul>
  </header>

  <div data-router>

  </div>

  <script src="./router.js"></script>
  <script src="./routes.js"></script>
  <script src="./index.js"></script>
</body>

</html>
```

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Creamos nuestras Rutas

```js
const routes = [
  {
    path: '/',
    template: '<h1>Hola</h1>'
  },
  {
    path: '/contact',
    template: '<h1>Contacto</h1>'
  },
  {
    path: '/about',
    template: '<h1>Acerca de mi</h1>'
  },
];
```

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Creacion del Router

Creamos la clase Router

```js
class Router {

  constructor(routes) {
    this.routes = routes;
    this._loadInitialRoutes();
  }
}
```

Nos interesa que al iniciar el enrutador se encargue de verificar nuestra ubicacion actual.

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Creamos la function _loadInitialRoutes

```js
_loadInitialRoute() {
  const pathNameSplit = window.location.pathname.split('/');
  const pathSegments = pathNameSplit.length > 1 ? pathNameSplit.slice(1) : '';

  console.log(pathSegments);
  this.loadRoute(...pathSegments);
}
```

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Creamos nuestra funcion para hacer match de la URL

```js
_matchUrlToRoute(urlSegments) {
  const matchedRoute = this.routes.find(route => {
    const routePathSegments = route.path.split('/').slice(1);
    if (routePathSegments.length !== urlSegments.length) {
      return false;
    }
    return routePathSegments.every((routePathSegment, i) => routePathSegment === urlSegments[i]);
  });
  return matchedRoute;
}
```

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Creamos la funcion para cargar la ruta

```js
loadRoute(...urlSegments) {
  const matchedRoute = this._matchUrlToRoute(urlSegments);
  const url = `/${urlSegments.join('/')}`;
  history.pushState({}, 'this works', url);
  const routerOutElement = document.querySelectorAll('[data-router]')[0];
  routerOutElement.innerHTML = matchedRoute.template;
}
```

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Agregamos nuestrp Index.js

```js
const router = new Router(routes);
```

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Router terminado

```js
class Router {

  constructor(routes) {
    this.routes = routes;
    this._loadInitialRoute();
  }

  loadRoute(...urlSegments) {
    const matchedRoute = this._matchUrlToRoute(urlSegments);
    const url = `/${urlSegments.join('/')}`;
    history.pushState({}, 'this works', url);
    const routerOutElement = document.querySelectorAll('[data-router]')[0];
    routerOutElement.innerHTML = matchedRoute.template;
  }

  _matchUrlToRoute(urlSegments) {
    const matchedRoute = this.routes.find(route => {
      const routePathSegments = route.path.split('/').slice(1);
      if (routePathSegments.length !== urlSegments.length) {
        return false;
      }
      return routePathSegments.every((routePathSegment, i) => routePathSegment === urlSegments[i]);
    });
    return matchedRoute;
  }

  _loadInitialRoute() {
    const pathNameSplit = window.location.pathname.split('/');
    const pathSegments = pathNameSplit.length > 1 ? pathNameSplit.slice(1) : '';

    console.log(pathSegments);
    this.loadRoute(...pathSegments);
  }
}
```

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Comentarios

Este enrutador es muy sencillo pero tiene muchisimos fallos de funcionalidad, la idea de este curso es unicamente demostrar las bases del comportamiento de un enrutador de libreria, sin embargo este no es recomendable que sea usado en produccion.

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>