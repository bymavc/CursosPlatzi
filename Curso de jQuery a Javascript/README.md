# Curso de jQuery a JavaScript<!-- omit in toc -->

## Tabla de Contenido<!--omit in tox -->
- [Tabla de Contenido](#tabla-de-contenido)
- [Introduccion](#introduccion)
- [Problema](#problema)
- [Ventajas de usar Javascript](#ventajas-de-usar-javascript)
- [Procesos asincronos](#procesos-asincronos)
- [Variables](#variables)
- [Funciones](#funciones)
- [Promesas](#promesas)
- [Timers](#timers)
- [Ajax](#ajax)
- [Funciones asincronas](#funciones-asincronas)
- [Selectores](#selectores)

## Introduccion

jQuery es una libreria de Javascript que resuelve:
* Una misma forma de acceder al DOM `$('selector')`: En ese tiempo, todos los navegadores accedian al DOM de una forma diferente.
* Poder interactuar con datos de un servidor `$.ajax()`: jQuery permite hacer llamadas al servidor.
* Crear animaciones `$.animate()`: En ese tiempo crear animaciones era muy dificil.

<div align="right">
  <small><a href="##tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Problema
* Se empezo a abusar de la libreria y se empezo a usar sin ver si realmente era necesario su uso o no.
* Uno se hacia dependiente de jQuery y sus sub-librerias a tal punto que cuando se queria modificar algo de una libreria no sabia como hacerlo.
* No se diferenciaba que era jQuery y que Javascript.
* Mientras unos de quedaban en jQuery, la revolucion de Javascript estaba sucediendo.

La idea es no depender de una libreria sino aprender la tecnologia que esta detras de cada libreria.

<div align="right">
  <small><a href="##tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Ventajas de usar Javascript
* Reutilizar conocimiento en otros lados de tu aplicacion.
* Poder implementar soluciones sin depender de una libreria.
* Estar mas capacitado para grandes empresas.

<div align="right">
  <small><a href="##tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Procesos asincronos

Un proceso asincrono es un codigo que se esta ejecutando, pero no ha terminado de ejecutarse antes de que se ejecute el codigo que esta despues de el.

Esto permite que la aplicacion no se cuelgue mientras esta ejecutando un proceso muy largo.

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Variables
* `var` es la forma de crear variables hasta ES5.
* `const` es para declarar constantes.
* `let` es para crear variables que cambian.

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Funciones 
```js
function cambiarNombre(nuevoNombre) {
  cambia = nuevoNombre;
}

// Desde ES6, las funciones se pueden declarar como arrow functions.
cambiarNombre = (nuevoNombre) => {
  cambia = nuevoNombre;
}
```

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Promesas

Una promesa es un objeto que representa la terminacion o el fracaso eventual de una operacion asincrona.

```js
// Crear una promesa
const getUser = new Promise(function(todoBien, todoMal) {
  // llamar a un API
  todoBien("todo bien");
});

// Consumir una promesa
getUser
  .then(function(msn) {
    // maneja cuando la promesa functiona correctamente
  })
  .catch(function(msn) {
    // maneja cuando hay un error en la promesa
  });

// Consumir varias promesas a la vez.
// EL then se ejecuta cuando terminen todas las promesas.
// El catch se ejecuta en el primer error.
Promise.all([
  promesa1,
  promesa2
])
.then(function() {})
.catch(function() {});

// Se ejecuta el then de la promesa que termine primero.
Promise.race([
  promesa1,
  promesa2
])
.then(function() {})
.catch(function() {});
```

Una promesa puede retornar otra promesa.

Las promesas resuelven el problema del Callback Hell haciendo haciendo que una promesa pueda devolver otra promesa y en lugar de ser anidadas como los callback, estas promesas son encadenadas.

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Timers
* `setInterval()` se ejecuta cada cierto tiempo.
* `setTimeout()` se ejecuta una sola vez luego de un periodo de tiempo .

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Ajax

**jQuery**

```js
$.ajax("url", {
  method: "GET", // POST, PUT, DELETE
  success: function(data) {
    // se ejecuta cuando todo sale bien
    // data: lo que devuelve el API
  },
  error: function(error) {
    // se ejecuta cuando hay un error
    // error: mensaje de error del API
  }
});
```

**Javascript**

```js
fetch("url")
  .then(function(reponse) {

  })
  .catch(function(response) {

  });
```

Fetch devuelve una promesa. Esta promesa, a su vez, tiene un metodo llamado `json()` que regresa otra promesa con los datos en formato JSON.

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Funciones asincronas

Una funcion asincrona va a ser como una funcion normal, pero poniendo codigo asincrono de forma que sea mas facil de leer de forma sincrona.

Para declarar una funcion asincrona se una `async` / `await`:
* async: declara que una funcion es asincrona.
* await: indica que se debe de terminar con el fragmento de codigo para continuar con la ejecucion de la funcion.

```js
async function load() {
  const response = await fetch("url");
}
```

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Selectores

Los selectores nos permiten seleccionar los elementos del DOM con el fin de poder manipularlos.

Por convencion, las variables que son elementos del DOM comienzan con una `$`.

**jQuery**

```js
const $home = $(".home"); // Elemento de la clase home
const $home = $("#home"); // Elemento con el id home
```

**Javascript**

```js
// Retorna un elemento con el id home
document.getElementById("home");

// Retorna una lista de elementos con la clase home
document.getElementsByClassName("home");

// Retorna una lista de elementos con el tag div
document.getElementsByTagName("div");

// Retorna el primer elemento que coincida con el query de busqueda
document.querySelector("div .home #modal");

// Retorna una lista con todos los elementos ue coincidan con el query de busqueda
document.querySelectorAll("div .home #modal");
```

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>