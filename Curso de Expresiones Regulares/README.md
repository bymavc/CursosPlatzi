# Curso de Expresiones Regulares <!-- omit in toc -->

## Tabla de Contenido<!--omit in toc -->

- [Tabla de Contenido](#tabla-de-contenido)
- [Introduccion](#introduccion)
- [Que son las expresiones regulares](#que-son-las-expresiones-regulares)
- [Aplicaciones de las expresiones regulares](#aplicaciones-de-las-expresiones-regulares)
  - [Enlaces de interes](#enlaces-de-interes)
- [Introduccion al Lenguage de las expresiones regulares](#introduccion-al-lenguage-de-las-expresiones-regulares)
  - [Enlaces de interes](#enlaces-de-interes-1)
- [El caracter (.)](#el-caracter)
- [Las clases predefinidas y construidas](#las-clases-predefinidas-y-construidas)
- [Los delimitadores: +, *, ?](#los-delimitadores)
  - [Ejemplo](#ejemplo)
- [Los contadores {1,4}](#los-contadores-14)
  - [Ejemplo](#ejemplo-1)
- [El caso de (?) como delimitador](#el-caso-de--como-delimitador)
  - [Ejemplo](#ejemplo-2)
- [Not(^), su uso y sus peligros](#not-su-uso-y-sus-peligros)
  - [Ejemplo](#ejemplo-3)
- [Reto: Filtrando letras en numeros telefonicos utilizando negaciones](#reto-filtrando-letras-en-numeros-telefonicos-utilizando-negaciones)
- [Principio (^) y final de linea ($)](#principio--y-final-de-linea)
- [URLs](#urls)
- [Mails](#mails)

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Introduccion

Este curso te va a enseñar qué son las expresiones regulares y cómo utilizarlas.
Por ejemplo aplicaciones de búsqueda y filtrado, las expresiones regulares son extremadamente potentes, aprende a utilizarlas en este curso.

>  Dicen que cuando tienes un problema y lo intentas solucionar con Expresiones regulares tienes dos problemas.
>

Falso.

Aunque las expresiones regulares pueden ser un poco intimidantes en un principio, son un herramienta que todo desarrollador *Independientemente del lenguaje de programación de su preferencia* debe de traer SIEMPRE en la mochila.

Las expresiones regulares, fuera de las definiciones teóricas, se basan en un lenguaje aunque ha evolucionado desde hace más de medio siglo, sigue siendo el mismo desde los 80 Y TODO EL MUNDO LOS USA.

Sirven para crear patrones de búsqueda de texto y las herramientas (y lenguajes) que las utilizan se usan para tratar desde grandes volúmenes de datos hasta corroborar que una dirección de email está bien escrita.

Tratar, por ejemplo un archivo de más de 2 millones de líneas y 120 megas en menos de 2 segundos, nada mal, ¿no crees?

No sólo es copiar y pegar lo que parecen ser puntos, líneas, asteriscos, signos de interrogación que parecen tener ningún sentido de stack overflow, sino entender exactamente qué hace cada uno y crear los tuyos.

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Que son las expresiones regulares

Las expresiones regulares son patrones de caracteres que te permite ir seleccionando o descartando datos en un archivo de texto como por ejemplo csv, o en una línea o un input, según coincidan o nó con este patrón.

Prácticamente todos los lenguajes de programación tienen librerías o módulos para manejar expresiones regulares.

Las expresiones regulares pueden ser muy complejas pero no son nada difíciles de entender.

A través de este curso, sin tecnicismos y con ejemplos puntuales, vamos a aprender a utilizarlas para que sean esa herramienta que siempre nos ayude, y sea la primera para solucionar problemas de grandes cantidades de datos en string.

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Aplicaciones de las expresiones regulares

Buscar e investigar sobre Expresiones Regulares puede ser muy intimidante.

```js
/^(.){5}\w?[a-Z|A-Z|0-9]$/ig
```

En serio pueden parecer muy, muy raras; pero la verdad es que no lo son.

En esta clase aprenderás, para qué te puede servir el saber usar bien las Expresiones Regulares; y es, en pocas palabras, para buscar.

### Enlaces de interes

A Ruby regular expression editor:  [https://rubular.com/](https://rubular.com/)

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Introduccion al Lenguage de las expresiones regulares

Con las expresiones regulares vamos a solucionar problemas reales, problemas del día a día.

¿Qué pasa si queremos buscar en un texto (txt, csv, log, cualquiera), todos los números de teléfonos que hay?
Tendríamos que considerar por ejemplo, que un teléfono de México serían 10 dígitos; hay quienes los separan con guión, hay quienes los separan con puntos, hay quienes no los separan sino que tienen los 10 dígitos exactos, y este patrón puede cambiar para otros países.

Esto mismo sucede con números de tarjetas de crédito, códigos postales, dirección de correos, formatos de fechas o montos, etc.

### Enlaces de interes

App REGEX en linea:  [https://regex101.com/](https://regex101.com/)

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## El caracter (.)

Una cadena de caracteres es un conjunto de caracteres en sucesion, para las computadoras incluso el espacio en blanco es un caracter representado en codigo (normalmente ASCII). El caracter (.) en particular representa cualquier caracter, al utilizarlo en una expresion regular le estaresmos indicando que busque todo aquello que sea un caracter.

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Las clases predefinidas y construidas

Las búsquedas en las expresiones regulares funcionan en múltiplos de la cantidad de caracteres que explícitamente indicamos.

- \d = Todos los caracteres numericos
- \w = Numeros y letras sin caracteres especiales 0-9, A-Z, a-z y _
- \s = Espacio en blanco
- [0-9] = Encuentra los digitos incluidos en el rango (del 0 al 9)
- [a-zA-Z0-9_] = Encuentra los caracteres en el rango, equivale a \w
- [a-fA-F0-9] = Hexadecimal

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Los delimitadores: +, *, ?

- (*) = ninguno o mas
- (+) = uno o mas
- (?) = ninguno o uno

### Ejemplo

```js
// Busca una letra de la "a" a la "z" con 0 o mas digitos por delante

\d*[a-z] 
```

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Los contadores {1,4}

Podemos generalizar nuestras búsquedas, a ser específicos cubriendo grandes cantidades caracteres sin tener que escribir de forma repetitiva como sería poner por ejemplo "\d\d\d\d\d\d\d\d…".

Este delimitador te permite indicar la cantidad minima del caracter especificado y la cantidad maxima del caracter especificado.

### Ejemplo

```js
// Busca grupos de al menos dos digitos y de maximo 4 digitos

\d{2,4}

// Busca grupos de 4 o mas digitos

\d{4,}

// Ejemplo para numeros de telefono
// [+]? ninguno o un signo de mas en caso de codigo de pais
// \d{2,9} grupo de 4 a 9 digitos
// [ \-\.]? ninguno o un punto, espacio o guion al final de cada grupo de digitos
// {2,4} Repetible minimo dos y maximo 4 veces

[\+]?(\d{2,9}[ \-\.]?){2,4}
```

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## El caso de (?) como delimitador

El ? indica al patrón que encuentre las coincidencias de manera rápida (o greedy); es decir, devolviendo el resultado más pequeño que haga match hasta donde se encuentra el delimitador, y esto lo haga tantas veces como sea posible dentro de la cadena.

### Ejemplo

```js
// Para lineas de csv 
// Busca cualquier coincidencia de uno o mas caracteres que esten antes de una coma (,) o un espacio en blanco (\n)

.+?[,\n]{1,1}
```

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Not(^), su uso y sus peligros

Este caracter nos permite negar una clase o construir “anticlases”, vamos a llamarlo así, que es: toda la serie de caracteres que no queremos que entren en nuestro resultado de búsqueda.

Para esto definimos una clase, por ejemplo: [0-9], y la negamos [^0-9] para buscar todos los caracteres que coincidan con cualquier caracter que no sea 0,1,2,3,4,5,6,7,8 ó 9.

- \D = Todo lo que no sea numero
- \W = Todo lo que no sean numeros, letras ni underscore (_)
- \S = Todo lo que no sea espacio en blanco

### Ejemplo

```js
// Todo lo que no se encuentre entre "0" y "5", etre "a" y "c" o sea espacio

[^0-5a-c ]

555658
56-58-11
56.58.11
56.78-98
65 09 87
76y87r98

// Todas las parejas de numeros que esten separados por caracteres que no sean numeros

\d\d\D?*
```

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Reto: Filtrando letras en numeros telefonicos utilizando negaciones

## Principio (^) y final de linea ($)

Estos dos caracteres indican en qué posición de la línea debe hacerse la búsqueda:
el ^ se utiliza para indicar el principio de línea
el $ se utiliza para indicar final de línea

^ ------------- $

- ^ = Inicio de Linea
- $ = Final de Linea

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## URLs

Una de las cosas que más vamos a usar en la vida, seamos frontend o backend, serán directamente dominios o direcciones de internet; ya sea direcciones completas de archivo (una url) o puntualmente dominios para ver si es correcto un mail o no.

```js
// http: Debe tener http
// s?: puede incluir una s
// \/: es necesario escapar el backslash
// [\w\-\.]+: es una clase que pude contener letras, dashes y puntos.

https?:\/\/[\w\-\.]+\.\w{2,5}\/?\S*

```

san@san.com

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Mails

Quedamos en que ya podemos definir URLs, y dentro de las URLs están los dominios. No es infalible, pero es muy útil para detectar la gran mayoría de errores que cometen los usuarios al escribir sus emails.

```js
// Usuario

[\w\._\-]{2,30}\+?[\w\._\-]{0,10}@


// Dominio

@[\w\-]{2,}\.\w{2,5}


// Email completo

/^[\w\._\-]{2,30}\+?[\w\._\-]{0,10}@[\w\-]{2,}\.\w{2,5}$/

```

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>