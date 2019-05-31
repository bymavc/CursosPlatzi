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
- [Templates](#templates)
- [Usando Templates](#usando-templates)
- [Eventos](#eventos)
- [Clases y estilos CSS](#clases-y-estilos-css)
- [Creacion de elementos](#creacion-de-elementos)
- [Asignacion de Atributos](#asignacion-de-atributos)
- [Formularios](#formularios)
- [Desestructuracion de objetos](#desestructuracion-de-objetos)
- [Dataset](#dataset)
- [Transformar tipos de datos](#transformar-tipos-de-datos)
- [Encontrar elementos en lista (find)](#encontrar-elementos-en-lista-find)
- [Switch](#switch)
- [Manejo de errores](#manejo-de-errores)
- [Guardar datos en cache](#guardar-datos-en-cache)
- [Obtener datos del cache](#obtener-datos-del-cache)

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

## Templates

**jQuery**

En jQuery se tiene que poner todo el html dentro de una cadena de texto.

```js
function videoItemTemplate(src, title) {
  return (
    '<div class="primaryPlaylistItem">' + 
      '<div class="primaryPlaylistTiem-image">' + 
        '<img src="' + src + '">' + 
      '</div>' + 
      '<h4 class="primaryPlaylistItem-title">' + 
        title + 
      '</h4>' +
    '</div>'
  );
}
```

**Javascript**

Se usa ua caracteristica de ES6 llamada `template literals`.

```js
function videoItemTemplate(src, title) {
  return (
    `<div class="primaryPlaylistItem">
      <div class="primaryPlaylistItem-image">
        <img src="${src}">
      </div>
      <h4 class="primaryPlaylistItem-title">
        ${title}
      </h4>
    </div>`
  );
}
```

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Usando Templates

La plantilla no puede ser llamada de frente puesto que en el html se mostraria como texto. Primero se hace una transformacion de la plantilla para recien agregarla al contenedor que se desee.

```js
function titleTemplate(title) {
  return (
    `<h1>${title}</h1>`
  );
}

// Se trae la plantilla y se guarda en ua variable.
const HTMLString = titleTemplate(movie);
// Se crea un documento html vacio
const html = document.implementation.createHTMLDocument();
// Se agrega la plantilla al innerHTML del coumento html
// esto hace que la plantilla en texto se convierta a elementos DOM
html.body.innerHTML = HTMLString;
// Se agrega el primer hijo (que es donde se encuentra la plantilla) al contenedor donde se quiere agregar la plantilla
$actionContainer.append(html.body.children[0]);
```

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Eventos

Son una forma de notificar a la aplicacion cuando algo interesante ha sucedido.

**jQuery**

```js
$("div").on("click", function(event) {

});
```

**Javascript**

```js
const $element = document.getElementById("element");
$element.addEventListener("click", function(event) {

});
```

**Nota**: cuando se activa el evento submit, el browser se refresca por defecto. Para evitar esto se usa `event.preventDefault()`.

Para ver la lista de eventos:
http://developer.mozilla.org/en-US/docs/Web/Events

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Clases y estilos CSS

**Clases**

```js
// Agrega una clase
$element.classList.add("clase");

// Remueve una clase
$element.classList.remove("clase");

// Intercambia entre agregar y remover una clase
$element.classList.toggle("clase");
```

**Estilos inline**

```js
modal.style.animation = "modalOut .8s forwards";
```

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Creacion de elementos

```js
const $loader = document.createElement("img");
```

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Asignacion de Atributos

**jQuery**

```js
$("#element").attr({
  src: "",
  height: ""
});
```

**Javascript**

```js
const $element = document.getElementById("element");

// setear el atributo en un elemento DOM
$element.setAttribute("src", "img/foto.png");

// obtener un atributo de un elemento DOM
const src = $element.getAttribute("src");
```

Tambien se puede crear una funcion para asignar multiples atributos a un elemento DOM.

```js
function setAttributes($element, attributes) {
  for(const attribute in attributes) {
    $element.setAttribute(attribute, attributes[attribute]);
  }
}
```

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Formularios

`FormData()` es una interfaz que te permite obtener los valores de un formulario.

```js
// FormData va a abstraer todos los valores de los elementos del formulario que cuenten con un atributo 'name' asignado y los va a setear en un objeto de tipo FormData.
const data = new FormData($form);

// Retorna el valor del elemento con el atributo name="nombre"
data.get("nombre");

// Setea el valor avengers en la key pelicula 
data.set("pelicula", "avengers");
```

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Desestructuracion de objetos

`Desestructuring assignment` permite entrar a un objeto o lista y poder sacar un dato para asignarlo a otra variable.

```js
// el fetch devuelve una promesa con la siguiente estructura: promesa.data.movies
// con el destructuring assignment estamos creando una variable que se llama pelis y solo contiene la informacion de movies.
const {
  data: {
    movies: pelis
  }
} = await fetch(`api_url`);

// Lo anterior seria igual a esto:
const response = await fetch(`api_url`);
const pelis = response.data.movies;
```

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Dataset

`Dataset` permite acceder a un objeto con todos los atributos `data` de un elemento DOM.

```html
<div id="element" data-id="10" data-category="action"></div>
```

```js
const $element = document.getElementById("element");

// guarda el valor de data-id
const id = element.dataset.id;
//guarda el valor de data-category
const category = $element.dataset.category;
```

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Transformar tipos de datos

Cambiar un string de datos

```js
// parseInt("numero", base)
let n = parseInt("500", 10);

// tambien se puede usar el double not bitwise operator.
let n2 = ~~"500";
```

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Encontrar elementos en lista (find)

`find()` devuelve el primer elemento de un array que cumpla con el criterio de busqueda. Si no se encuentra ningun elemento devuelve undefined.

```js
function find(list, id) {
  return list.find(movie => movie.id === id);
}
```

Informacion referencial:
https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Array/find

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Switch

```js
switch(category) {
  case "action": {
    // codigo de action
  }
  case "drama": {
    // codigo de drama
  }
  default: {
    // codigo por defecto
  }
}
```

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Manejo de errores

El manejo de errores se hace con un bloque `try/catch`. Se intenta ejecutar un bloque de instrucciones (try) y se especifica una respuesta en caso de que suceda algun error (catch).

```js
try {
  // codigo a evaluar
}
catch(error) {
  // codigo por si sucede algun error
  alert(error.message);
}
```

* Se puede crear un error customizado con `Error()`.
* Se puede lanzar un error con `throw`.

```js
throw new Error('No se encontro ningun resultado');
```

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Guardar datos en cache

* `localStorage` permite almacenar datos sin tiempo de expiracion.
* `sessionStorage` permite almacenar datos. Estos datos se van a borrar cuando se termine la session del navegador.

En `localStorage` solo se puede guardar texto plano. No se pueden guardar objetos.

```js
// eliminar los datos
window.localStorage.clear();

// setear un valor
window.localStorage.setItem("nombre", "Miguel");

// setear un objeto
// primero se tiene que convertir el objeto en un string
window.localStorage.setItem("objeto", JSON.stringify({"peli": "wonder woman"}));

// obtener el valor de un key
window.localStorage.getItem("nombre");

// obtener el valor de un texto objeto y convertirlo en objeto
JSON.parse(window.localStorage.getItem("objeto"));
```

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Obtener datos del cache

Revisar si los datos se encuentran en cache.

```js
async function cacheExist(key) {
  const cacheList = window.localStorage.getItem(key);

  if(cacheList) return JSON.parse(cacheList);

  const data = await fetch("url");
  window.localStorage.setItem(key, JSON.stringify(data));
  return data;
}
```

Si se desea volver a traer los datos se puede hacer lo siguiente:
* Poner un boton que traiga los datos.
* Hacer un setTimeout que borre el localStorage.

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>