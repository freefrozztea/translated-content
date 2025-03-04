---
title: Date.prototype.toDateString()
slug: Web/JavaScript/Reference/Global_Objects/Date/toDateString
tags:
  - Fecha
  - JavaScript
  - Prototipo
  - Referencia
  - metodo
translation_of: Web/JavaScript/Reference/Global_Objects/Date/toDateString
original_slug: Web/JavaScript/Referencia/Objetos_globales/Date/toDateString
---
{{JSRef}}

El método **`toDateString()`** devuelve la porción de la fecha de un objeto {{jsxref("Date")}} en formato humano legible en Inglés Americano.

## Sintaxis

```
dateObj.toDateString()
```

### Valor devuelto

Una cadena que representa la porción de fecha de un determinado objeto {{jsxref("Date")}} en formato humano legible en Inglés Americano.

## Descripción

Las instancias de {{jsxref("Date")}} representan momentos especificos en el tiempo. Un llamado a {{jsxref("Date.prototype.toString()", "toString()")}} devolverá la fecha formateada en un formato humano legible en Inglés Americano. En [SpiderMonkey](/es/docs/SpiderMonkey), esto consiste en la porción de la fecha (día, mes, y año) seguido por la porción de la hora (horas, minutos, segundos, y zona horaria). Algunas veces sólo se necesita obtener una cadena de la porción de la hora; esto puede lograrse con el método `toTimeString()`.

El método `toDateString()` es especialmente útil, pues los distintos motores compatibles que implementan [ECMA-262](/es/docs/ECMAScript) pueden diferir en la cadena obtenida al ejecutar {{jsxref("Date.prototype.toString()", "toString()")}} para los objetos de tipo {{jsxref("Date")}}, pues dicho formato depende de la implementación, por lo que es posible que el enfoque de la segmentación simple de cadenas no produzca resultados consistentes entre distintos motores.

## Ejemplos

### Uso básico de `toDateString()`

```js
var d = new Date(1993, 5, 28, 14, 39, 7);

console.log(d.toString());     // logs Wed Jun 28 1993 14:39:07 GMT-0600 (PDT)
console.log(d.toDateString()); // logs Wed Jun 28 1993
```

> **Nota:** Los meses son 0-indexados cuando son utilizados como parámetros de {{jsxref("Date")}} (Siendo así, el cero (0) corresponde a Enero y el once (11) a Diciembre).

## Especificaciones

| Epecificación                                                                                                            | Estatus                      | Comentario          |
| ------------------------------------------------------------------------------------------------------------------------ | ---------------------------- | ------------------- |
| {{SpecName('ES3')}}                                                                                                 | {{Spec2('ES3')}}         | Definición inicial. |
| {{SpecName('ES5.1', '#sec-15.9.5.3', 'Date.prototype.toDateString')}}                             | {{Spec2('ES5.1')}}     |                     |
| {{SpecName('ES6', '#sec-date.prototype.todatestring', 'Date.prototype.toDateString')}}     | {{Spec2('ES6')}}         |                     |
| {{SpecName('ESDraft', '#sec-date.prototype.todatestring', 'Date.prototype.toDateString')}} | {{Spec2('ESDraft')}} |                     |

## Compatibilidad entre navegadores

{{Compat("javascript.builtins.Date.toDateString")}}

## Vea también

- {{jsxref("Date.prototype.toLocaleDateString()")}}
- {{jsxref("Date.prototype.toTimeString()")}}
- {{jsxref("Date.prototype.toString()")}}
