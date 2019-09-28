### Consola

- [@ChromeDevTools en Twitter](https://twitter.com/chromedevtools?lang=es)
- [Chrome DevTools](https://developer.chrome.com/devtools)
- [Chrome DevTools v2](https://developers.google.com/web/tools/chrome-devtools/?hl=es)

**Métodos:**
- `.assert()` *Aparece un mensaje de error en la consola si la afirmación es falsa.*:

  ```javascript
  var controlador = false;
  console.assert(controlador, "\"controlador\" es igual a \"false\"");
  ```

- `.clear()` *Limpia la consola*:

  ```javascript
   console.clear()
  ```


- `.dir()` *Retorna una lista interactiva de las propiedades de un objeto*:

  ```javascript
  console.dir(document.body);
  ```

- `.dirxml()` *Retorna una representación HTML del objeto*:

  ```javascript
   console.dirxml(document.body);
  ```


- **Agrupadores**:
  - `.group()` *Crea un grupo de mensajes de consola*:

    ```javascript
       console.group("bucleFor");
       for(var i=100; i>0; i--){
         console.info("Iteración numero %i", i)
       }
       console.groupEnd();
    ```

  - `.groupCollapsed()` *Crea un grupo de mensajes de consola minimizados (por defecto)*:

    ```javascript
    console.groupCollapsed("bucleFor");
    for(var i=100; i>0; i--){
      console.info("Iteración numero %i", i)
    }
    console.groupEnd();
    ```

  - `.groupEnd()` *Cierra el grupo de mensajes*:

    ```javascript
    console.group("bucleFor");
    for(var i=100; i>0; i--){
      console.info("Iteración numero %i", i)
    }
    console.groupEnd();
    ```

- **Tablas**:
  - `.table()` *Muestra los datos dentro de una tabla*:

    ```javascript
    var lenguajes = [
       { nombre: "JavaScript", extension: ".js" },
       { nombre: "TypeScript", extension: ".ts" },
       { nombre: "CoffeeScript", extension: ".coffee" }
    ];
   
    console.table(lenguajes);
   
    console.table(lenguajes, "extension");
    ```

- **Gestión del tiempo**:
  - `.time()` *Inicia un contador en ms*:
  - `.timeEnd()` *Para el contador y devuelve el resutlado*:

    ```javascript
    console.time("Medición de miArray");
    var miArray = new Array(1000000);
    for (var i = miArray.length - 1; i >= 0; i--) {    
     miArray[i] = new Object();
    };
    console.timeEnd("Medición de miArray");
    ```

- **Notificadores**:
  - `.log()` *Saca un mensaje por consola*:

    ```javascript
    console.log("Hola en formato clásico");
    ```

  - `.info()` *Similar a console.log*:

    ```javascript
    console.info("Hola en formato informativo");
    ```

  - `.warn()` *Similar a Console.log*:

    ```javascript
    console.warn("Hola en formato alerta");
    ```

  - `.error()` *Similar a console.log, invcluye *:

    ```javascript
    console.error("Hola en formato error");
    ```

- **Formateadores**:

Formato | Descripción
------------ | -------------
%s | Cadena
%d o %i | Número entero
%f | Decimal
%o | DOM
%O | Objeto js
%c | CSS

- Ejemplos:
  - `%o` para estrcuturas del DOM

    ```javascript
    var parrafos = document.getElementsByTagName("p");
    console.log("DOM: %o", parrafos);
    ```

  - `%O` para objectos JS

    ```javascript    
    var objeto = {"nombre":"Yo","Apellido":"Mismo"};
    console.log("Objeto: %O", objeto);
    ```

  - usando CSS:

    ```javascript
    console.log('Esto es aburrido...');
    console.log('%c Pero se puede mejorar fácilmente! ', 'background: #3EBDFF; color: #FFF; font-size:25px;');
    ```
 
### Caracteres especiales:

- `\t` *Tabulador*
- `\'` *Comillas Simples*
- `\"` *Comillas Dobles*
- `\\` *\*
- `\n` *Salto de línea*

```javascript
function caracteresDemo () {
  console.log("Hasta aquí... todo correcto. Ahora vamos a \"tabular\":\tves? Ya estamos más lejos.\n\'Otra linea ;-)\'")
};
```

### Comentarios
- Una línea

  ```javascript
  // Comentario en una línea
  ```

- Multiples Líneas

  ```javascript
  /*
  Una Línea....
  Otra linea...
  Etc...
  */
  ```

- [JSDoc](https://en.wikipedia.org/wiki/JSDoc)

### Variables

- No se pueden usar espacios

  ```javascript
  var con espacios = 1;
  ```

- No usar un número delante

  ```javascript
  var 1numero = 1;
  ```

- Válidos, pero no recomendado

  ```javascript
  var con_guiones_bajos = 1;
  var dame$ = 1;
  ```

- Válidos, es mejor usar [camelCase](https://es.wikipedia.org/wiki/CamelCase)

  ```javascript
  var otraOpcion = 1;
  var opcionCon123123 = 1;
  ```


### Tipos de variables

Operador `typeof` y su [especificación](http://www.ecma-international.org/ecma-262/5.1/#sec-11.4.3)

- [x] Undefined

  ```javascript
  typeof undefined
  typeof noDefinido
  typeof tampocoCreado
  ```

- [x] Object

  ```javascript
  typeof null
  typeof [15, 4]
  typeof new Date()
  typeof {a:1}
  ```

- [x] Boolean

  ```javascript
  typeof false
  typeof true
  typeof Boolean(false)
  ```

- [x] Number

  ```javascript
  typeof 3
  typeof 3.14
  typeof NaN
  typeof Infinity
  ```

- [x] String

  ```javascript
  typeof "hola"
  ```

- [x] Function

  ```javascript
  typeof function(){}
  ```

- [x] Symbol (ECMA6)

  > Ahora tenemos los símbolos, nuevo tipo de datos que sirve como identificador único para atributos de objetos
  > [EcmaScript 6: Símbolos](http://miguelsr.js.org/2015/08/20/es6-symbols.html) de [Miguel Sánchez](http://miguelsr.js.org/about/)

  ```javascript
  typeof Symbol()
  typeof Symbol('simbolo')
  ```


### Matemáticas Básicas

```javascript
var suma = 5 + 4;
var resta = 10 - 6;
var multiplicacion = 3 * 3;
var division = 6 / 2;
var modulo = 43 % 10;

function calcular (operacion) {
  console.log(operacion);
};
```

### Matemáticas Básicas (Agrupando operaciones)

```javascript
var expresion1 = (3 + 7) * 10;
var expresion2 = (-56 * 6) - 74 * -25;
var expresion3 = (3 * 3) + 10 - 12 / 2;
var expresion4 = 44 + (83 % (33 + 100));
var expresion5 = -145 + (500 / 10 - 5) + 10 * 10 ;

function calcular (operacion) {
  console.log(operacion);
};
```

### Matemáticas Básicas (crecimiento y decrecimiento)

```javascript
var numero = 5;

console.log(--numero); // 4
console.log(numero--); // 5 (luego 4)
console.log(++numero); // 6
console.log(numero++); // 5 (luego 6)
```

### Operadores de asignación
- = *Asignacion*
```javascript
var x = 1;
var y = 2;
x = y;
console.info("\"x\" vale ", x);
```

- += *Suma*
```javascript
var x = 1;
var y = 2;
x += y;
console.info("\"x\" vale ", x); // x = x + y
```

- -= *Resta*
```javascript
var x = 1;
var y = 2;
x -= y;
console.info("\"x\" vale ", x); // x = x - y
```

- *= *Multiplicación*
```javascript
var x = 1;
var y = 2;
x *= y;
console.info("\"x\" vale ", x); // x = x * y
```

- /= *División*
```javascript
var x = 1;
var y = 2;
x /= y;
console.info("\"x\" vale ", x); // x = x / y
```

- %= *Resto*
```javascript
var x = 1;
var y = 2;
x %= y;
console.info("\"x\" vale ", x); // x = x % y
```

**Jugando con variables**

```javascript
var empezoComo3 = 3;
era3();

empezoComo3 = 35;
era3();

empezoComo3 = empezoComo3 + 30;
era3();

empezoComo3 += 4;
era3();

empezoComo3++;
era3();

empezoComo3 -= 12;
era3();

empezoComo3--;
era3();

empezoComo3 *= 10;
era3();

empezoComo3 /= 11;
era3();

empezoComo3 += "texto";
era3();

empezoComo3 += 20;
era3();

empezoComo3++;
era3();


function era3 () {
    console.log("empezoComo3 debería ser 3, ahora su valor es " + empezoComo3);
};
```

### Interacción Básica con el Usuario

- `alert()`:

  ```javascript
  alert("¡Bienvenido a esta web!");
  ```

- `confirm()`:

  ```javascript
  confirm("¿Esta seguro que desea abandonar esta web?");
  ```

  **Ejemplo:**

  ```javascript
  var respuesta = confirm("presiona un botón!");
  if (respuesta === true) {
    console.log("Has aceptado!");
  } else {
    console.log("Has cancelado");
  }
  ```

- `prompt()`:

  ```javascript
  prompt("¿Como te llamas?");
  ```

- Registremos los datos en una variable:

  ```javascript
  var nombre = prompt("¿Como te llamas?");
  ```

### Modo Estricto

> El modo estricto hace varios cambios en la semántica normal de JavaScript. Primero, modo estricto elimina algunos errores silenciosos de JavaScript cambiando a que lance los errores. Segundo, modo estricto corrige errores que hacen que sea difícil para los motores de JavaScript para realizar optimizaciones: código de modo estricto a veces se puede hacer para correr más rápido que el código idéntico que no es estricto. Tercero, el modo estricto prohíbe sintaxis que es probable que sea definida en futuras versiones de ECMAScript.
> - [Mozilla](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Modo_estricto)

- [Compatibilidad](http://caniuse.com/#feat=use-strict)

En resumen:
- Detectaremos más errores
- Mejora la interpretación, lo que aumenta la velocidad de ejecucción.
- Previene que usemos sintaxis de futuras versiones de ECMAScript.

Aplicándolo a todo nuestro código

```javascript
// ./script.js
(function() {
  "use strict";

  // Nuestro código

})();
```

Aplicándolo solo en parte del código
```javascript
// ./script.js
function estricta(){
  'use strict';
  function anidada() {
    return "Yo también!";
  }
  return "Hola! Soy una función en modo estricto!  " + anidada();
}

function noEstricta() {
  return "yo no soy una función estricta.";
}
```

Algunos ejemplos:

- Error: Usar variables u objetos sin declararlos antes.

  ```javascript
  function estricto(){
    'use strict';
    pi = 3.14;
    console.log(pi);
  }
  ```

- Error: Borrar variables, objetos o funciones. 

  ```javascript
  function estricto(){
    'use strict';
    pi = 3.14;
    delete pi
  }
  ```

- Error: Duplicar parámetros

  ```javascript
  function estricto(){
    'use strict';
    function x (p1, p1){
      // código
    }
  }
  ```

- Error: Al usar carácteres escapados

  ```javascript
  function estricto(){
    'use strict';
    var x = \010; 
  }
  ```

Error: Al usar *writable:false*

```javascript
function estricto(){
  'use strict';
  var obj = {};
  Object.defineProperty(obj, "x", {value:0, writable:false});
  obj.x = 3.14;
}
```

Error: Al usar *with* 

```javascript
function estricto(){
  'use strict';
  with(document.getElementById('elemento').style) {
    backgroundColor = 'black';
    color = 'red';
    font_Size = '32px'; // Crea una variable global
   }
}
```

Error: Al usar *eval()* por seguridad

```javascript
function estricto(){
  'use strict';
  eval ("var x = 2");
  console.log(x);
}
```



Otras palabras reservadas en modo estricto:
- implements
- interface
- let
- package
- private
- protected
- public
- static


### Comparadores básicos

```javascript
var mayorQue = 100 > 10;
var menorQue = 10 < 100;
var mayorIgual = 100 >= 10;
var menorIgual = 10 <= 100;
var igual = 10 == 10;
var igualTotalmente = 10 === 10;
var noIgual = 100 != 10;

function comparar (dato) {
  console.log(dato);
};
```


### Comparadores complejos
- **AND(&&)**

  ```javascript
  var comparacion;
  comparacion = true && true; // true
  comparacion = true && false // false
  comparacion = false && false // false
  comparacion = false && true // false
  ```

- **OR(||)**

  ```javascript
  var comparacion;
  comparacion = true || true; // true
  comparacion = true || false // true
  comparacion = false || false // false
  comparacion = false || true // true
  ```

- Ejemplos:

  ```javascript
  var ex1 = true && true; // true
  var ex2 = (2 == 2) && (3 >= 6); // false
  var ex3 = (2>3) || (17 <= 40); // true
  var ex4 = false || false; // false
  
  function condicionalAvanzado ( paraComparar ) {
    if (paraComparar) {
      console.log("Verdadero!");
    } else {
      console.log("falso!");
    };
  };
  ```

### Otros datos

- Valor *real* es *true*:

```javascript
console.log("valor boleano de \"Fictizia\":", Boolean("Fictizia")  );
console.log("valor boleano de 1235:", Boolean(1235));
console.log("valor boleano de -1235:", Boolean(-1235));
console.log("valor boleano de un objeto:", Boolean({saludo: "hola"}));
console.log("valor boleano de un array:", Boolean(["platano", -1, false]));
console.log("valor boleano de un array:", Boolean(function(){}));
```

- Sin valor *real* es *false*:

```javascript
console.log("valor boleano de \"\":", Boolean("")  );
console.log("valor boleano de 0:", Boolean(0));
console.log("valor boleano de -0:", Boolean(-0));
console.log("valor boleano de null:", Boolean(null));
console.log("valor boleano de undefined:", Boolean(undefined));
console.log("valor boleano de NaN:", Boolean(NaN));
```

### Asignación por igualdad

```javascript
var administrador = 'Yo mismo';
var esAdministrador = (administrador === 'Yo mismo');
```
    
### If... else

- Estructura:

  ```javascript
  /* IF ...ELSE
  if (-algo verdadero-) {
    -ejecutaremos este código-
  } else {
    -Si lo anterior no era verdadero, se ejecutara este código-
  };
  */
  ```

- Documentación:
    - [If... else en w3schools](http://www.w3schools.com/js/js_if_else.asp)
    - [If... else en MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/if...else)

- Ejemplo:

  ```javascript
  if (true) {
    console.log("true, por eso me ejecuto");
  } else {
    console.log("false, por eso me ejecuto");
  }
  ```


### Else if...

```javascript
function testCondiccion (condicion){
  if (condicion == 1) {
    console.log("1, por eso me ejecuto");
  } else if (condicion == 2){
    console.log("2, por eso me ejecuto");
  } else {
    console.log("no es 1 o 2, por eso me ejecuto");
  }
}
```


### Switch

- Estructura:

  ```javascript
  /* Switch
  switch(expresión) {
    case n:
      //Código
      break;
    case n:
      //Código
      break;
    default:
      //Código
  }
  */
  ```

- Documentación:
    - [Switch en w3schools](http://www.w3schools.com/js/js_switch.asp)
    - [Switch en MDN](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Sentencias/switch)

- **Casos únicos:**

  ```javascript
  var nombre = "";
  switch (nombre) {
    case "Pepe":
      console.log("Hola Pepe");
      break;
    case "Luis":
      console.log("Hola Luis");
      break;
    case "Antonio":
      console.log("Hola Antonio");
      break;
    default:
      console.log('Ninguno de los nombres que pensamos... es '+nombre);
  }
  ```

- **Multiples coincidencias:**

  ```javascript
  var nombre = "";
  switch (nombre) {
    case "Pepe":
    case "Luis":
    case "Antonio":
      alert('Hola '+nombre);
      break;
    default:
      console.log('Ninguno de los nombres que pensamos... es '+nombre);
  }
  ```

### Operador Ternario (?:)

- Estructura:

  ```javascript
  /* 
  -- Una operación por caso --
  condicion ? expresion1 : expresion2 

  -- Multiples Operaciones por caso --
  condicion ? (
    operacion1,
    operacion2,
    otraoperacion
   ) : ( 
    operacion1,
    operacion2,
    otraoperacion
  );

  -- Evaluaciones multiples --
  condicion ? expresion1 : condicion2 ? expresion1 : expresion2;
  */
  ```

- Una operación por caso:

  ```javascript
  var esMiembro = true;
  console.info("El pago son  " + (esMiembro ? "20.00€" : "50.00€"));
  ```

- Evalución múltiple:

  ```javascript
  var esMiembro = true;
  var esAdulto = true;
  console.info(esMiembro ? "El pago son 20.00€" : esAdulto ? "Puedes enviar la solicitud cuando quieras" : "Tines que esperar aún. Lo siento.");
  ```

- Múltiples Operaciones:

  ```javascript
  var mensaje,
  esMiembro = true;
	
  esMiembro ? (
    mensaje = "El pago son 20.00€",
    console.info(mensaje)
  ) : (
    mensaje = "El pago son 50.00€",
    console.info(mensaje)
  );
  ```

### While

- Estructura:

  ```javascript
  /*  --while--
  while (-Condición-) {
    -Instrucciones-
  };
  */
  ```

- Documentación:
  - [While en w3schools](http://www.w3schools.com/js/js_loop_while.asp)
  - [While en MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/while)

- Bucle infinito:
  Este es un error muy común.

  ```javascript
  while (true) {
    console.log("Este texto se imprime hasta el infinito...");
  };
  ```

- Bucle que no se ejecutará:

  ```javascript
  while (false) {
    console.log("Este texto jamas se imprimirá...");
  };
  ```

- Ejemplo:

  ```javascript
  var control = 1;
  while (control <= 10) {
    console.log(control);
    control++;
  };
  ```


### For

- Estructura:

  ```javascript
  /*  --for--
  for (-Expresión inicial-; -Condición-; -Expresión Actualización-) {
    -Instrucciones-
  };
  */
  ```

- Documentación:
  - [For en w3schools](http://www.w3schools.com/js/js_loop_for.asp)
  - [For en MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for)
  - [Dominando el rendimiento](https://web.archive.org/web/20141205235948/https://blogs.oracle.com/greimer/entry/best_way_to_code_a)


- Ejemplo clásico:

  ```javascript
  for (var i = 0; i < 10; i++) {
    console.log(i);
  }
  ```

### Do... While

- Estructura:

  ```javascript
  /* --Do...while--
  do{
    -Instrucciones-
  } while (-Condición-);
  */
  ```

- Documentación:
  - [Do... While en w3schools](http://www.w3schools.com/js/js_loop_while.asp)
  - [Do... While en MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/do...while)

- Ejemplo:

  ```javascript
  var i = 0;
  do {
  i++;
    console.log(i);
  } while (i < 10);
  ```

- Al menos se ejecutará una vez, aunque la premisa no sea verdadera.

  ```javascript
  do{
    console.warn("me ejecuto")
  } while (false);
  ```

### Break y Continue

- *Continue* nos permite saltar parte del bucle.

  ```javascript
  for (var i = 0; i < 10; i++) {
    // Salta el 5 y sigue...
    if (i === 5) { 
      continue; 
  }
    console.log("El valor de i es "+i);
  }
  ```

- *Break* nos permite salir del bucle.

  ```javascript
  for (var i = 0; i < 10; i++) {
    // Llega a 5 y sale.
    if (i === 5) { 
        break; 
    }
    console.log("El valor de i es "+i);
  }
  ```

### Usos Avanzados

- Ejemplo usando decrecimiento:

  ```javascript
  for (var i = 10; i > 0; i--) {
    console.log(i);
  }    
  ```

- Ejemplo usando varios contadores:

  ```javascript
  for (var i = 0, x = 1, z = 2, tope = 10; i <= tope; x *= z, i++ ) {
    console.log("i vale "+i+", x vale "+x+", z vale "+z);
  }
  ```

### Números

**Librerías:**
- [Mathjs](http://mathjs.org/)

**Propiedades**

- [Notación científica](https://es.wikipedia.org/wiki/Notaci%C3%B3n_cient%C3%ADfica)

- `.MAX_VALUE` *El número más grande representable (1.7976931348623157e+308)*:

  ```javascript
  var numero1 = 1.7976931348623157e+308;
  var numero2 = 1.7976931348623157e+310;

  function verificarValorMaximo(num){
    if (num <= Number.MAX_VALUE) {
      console.log("El número no es infinito");
    } else {
      console.log("El número es infinito");
    }
  }
 
  verificarValorMaximo(numero1);
  verificarValorMaximo(numero2);    
  ```

- `.MIN_VALUE` *El número más pequeño representable (5e-324)*:

  ```javascript
  var numero1 = 5e-323;
  var numero2 = 5e-326;

  function verificarValorMinimo(num){
    if (num >= Number.MIN_VALUE) {
      console.log("El número no es infinito");
    } else {
      console.log("El número es infinito");
    }
  }

  verificarValorMinimo(numero1);
  verificarValorMinimo(numero2);
  ```

- `.NEGATIVE_INFINITY` *El valor negativo de la propiedad del objeto global Infinity*:

  ```javascript
  var numeroMinimo = (-Number.MAX_VALUE) * 2
  console.log(numeroMinimo);

  if (numeroMinimo === Number.NEGATIVE_INFINITY) {
    numeroMinimo = 0;
  }
  console.log(numeroMinimo);
  ```

- `.NaN` *Not A Number*:

  ```javascript
  NaN === NaN;      // false
  Number.NaN === NaN; // false
  isNaN(NaN);       // true
  isNaN(Number.NaN);  // true    
  ```

- `.POSITIVE_INFINITY` *Representa el infinito positivo*:

  ```javascript
  var numeroMaximo = Number.MAX_VALUE * 2
  console.log(numeroMaximo);

  if (numeroMaximo === Number.POSITIVE_INFINITY) {
    numeroMaximo = 0;
  }
  console.log(numeroMaximo);    
  ```

**Métodos:**

- `.toExponential()` *Devuelve una cadena con el valor número en formato de potencia*:

  ```javascript
  var numObj = 77.1234;
 
  console.log(numObj.toExponential());  // 7.71234e+1
  console.log(numObj.toExponential(4)); // 7.7123e+1
  console.log(numObj.toExponential(2)); // 7.71e+1
  console.log(77.1234.toExponential()); // 7.71234e+1   
  ```


- `.toFixed()` *Devulve un numero con decimales*:

  ```javascript
  var numObj = 12345.6789;

  numObj.toFixed();       //'12346' redondeo
  numObj.toFixed(1);      //'12345.7'
  numObj.toFixed(6);      //'12345.678900' Se añaden ceros en caso necesario
  (1.23e+20).toFixed(2);  //'123000000000000000000.00'
  (0).toFixed(2);         //'0.00'
  2.34.toFixed(1);        //'2.3' redondeo
  -2.34.toFixed(1);       //-2.3 Numeros negativos no son devueltos como cadenas.
  (-2.34).toFixed(1);     //'-2.3' En caso de usar paréntesis se salta la limitación 
  ```


- `.toLocaleString()` *Devulve una cadena con el valor numeral representado en lenguaje local*:

  ```javascript
  var numero = 3500;
  // En Local
  console.log(numero.toLocaleString()); // 3.500
  // En Árabe
  console.log(numero.toLocaleString('ar-EG')); // ٣٬٥٠٠
  // En Chino decimal
  console.log(numero.toLocaleString('zh-Hans-CN-u-nu-hanidec')); // 三,五〇〇
  ```


- `.toPrecision()` *Devuelve un numero precisado*:

  ```javascript
  var numero = 5.123456;

  console.log(numero.toPrecision());    // 5.123456
  console.log(numero.toPrecision(5));   // 5.1235
  console.log(numero.toPrecision(2));   // 5.1
  console.log(numero.toPrecision(1));   // 5
  console.log((1234.5).toPrecision(2)); // 1.2e+3 (En ocasiones )
  ```



- `.toString()` *Devuelve una cadena con el número en la base que determinemos*:

  ```javascript
  console.log((17).toString());     // '17'
  console.log((17.2).toString());   // '17.2'
  console.log((-0xff).toString(2)); // '-11111111'
  console.log((254).toString(16));  // 'fe'
  ```
 
- `.parseFloat()` *Devuelve un número décimal partiendo de una cadena*:

  ```javascript
  Number.parseFloat("3.14"); // 3.14
  Number.parseFloat("314e-2"); // 3.14
  Number.parseFloat("0.0314E+2"); // 3.14
  Number.parseFloat("3.14textos..."); // 3.14
  Number.parseFloat("1textos..."); //1
  ```
    
- `.parseInt()` *Devuelve un número entero en una base especifica o en base 10 partiendo de una cadena*:

  ```javascript
  parseInt(" 0xF", 16); // 15
  parseInt(" F", 16);  // 15
  parseInt("17", 8);  // 15
  parseInt(021, 8);  // 15
  parseInt("015", 10);  // 15
  parseInt(15.99, 10);  // 15
  parseInt("15,123", 10);  // 15
  parseInt("FXX123", 16);  // 15
  parseInt("1111", 2);  // 15
  parseInt("15*3", 10);  // 15
  parseInt("15e2", 10);  // 15
  parseInt("15px", 10);  // 15
  parseInt("12", 13);  // 15
  ```

### Math

**Métodos:**

- `.random()` *Devuelve un número aleatorio*

  ```javascript
  // Número aleatorio entre 0 (incluido) y 1 (excluido)
  Math.random(); 
  
  // Retorna un número aleatorio entre min (incluido) y max (excluido)
  Math.random() * (max - min) + min;
  Math.random() * (11 - 0) + 0;
  
  // Retorna un entero aleatorio entre min (incluido) y max (excluido)
  Math.floor(Math.random() * (11 - 0)) + 0;
  ```

- `.round()` *Devuelve el valor de un número redondeado al entero más cercano*

  ```javascript
  Math.round(20.5); // 21
  Math.round(20.49); // 20
  Math.round(-20.51); // -21
  ```

- `.floor()` *Devuelve el máximo entero menor o igual a un número.*

  ```javascript
  Math.floor(20.5); // 21
  Math.floor(20.49); // 20
  Math.floor(-20.51); // -21
  ```

- `.max()` *retorna el mayor de cero o más números*

  ```javascript
  function calcularMayor(valor1, valor2, valor3){
    return Math.max(valor1, valor2, valor3);
  }
  
  // Mejorando calcularMayor
  function calcularMayor(){
   var args = Array.prototype.slice.call(arguments);
   return Math.max.apply(null, args);
  }
  ```

- `.min()` *retorna el menor de cero o más números*

  ```javascript
  function calcularExtremos(){
    var args = Array.prototype.slice.call(arguments);
    return {minimo: Math.min.apply(null, args),
      maximo: Math.max.apply(null, args)
    };
  }

  misExtremos = calcularExtremos(1,2,4,56,-123);
  console.log("Mínimo: "+misExtremos.minimo+"\n"+"Máximo: "+misExtremos.maximo);
  ```    


### Dates

**Librerías:**
- [Momments.js](http://momentjs.com/)
- [Dates.js](http://www.datejs.com/)
- [JQuery timeAgo](http://timeago.yarp.com/)
- [Livestamp.js](https://mattbradley.github.io/livestampjs/)

**Metodos**

- Creando Fechas:
  - Fecha Actual:

    ```javascript
    var ahora = new Date();
    console.log(ahora);
    ```

  - Usando milisegundos (desde el 1/1/1970 00:00):

    ```javascript
    var diaDespues = new Date(3600*24*1000);
    console.log(diaDespues);
    ```

  - Usando cadenas de texto:

    ```javascript
    var newYear = new Date("January 1, 2016 00:00:00");
    ```

  - Usando números:

    ```javascript
      var newYear = new Date(2016, 1, 1); // AAAA, MM, DD
      var newYear = new Date(2016, 1, 1, 0, 0, 0); // AAAA, MM, DD, HH, MM, SS
    ```

  - Usando UTC:

    ```javascript
      var newYear = new Date(Date.UTC(2016, 1, 1));
    ```

- Getters:
  - Local
  
    ```javascript
    var ahora = new Date();
    console.log("La fecha es " + ahora);
    console.log("==== FECHA ====");
    console.log("El año: " + ahora.getFullYear()); // 4 digitos
    console.log("El mes: " + ahora.getMonth()); // 0 - 11
    console.log("El día de la semana: " + ahora.getDay()); // 0 - 6 (D - S)
    console.log("El día del mes: " + ahora.getDate()); // 1-31
    console.log("==== HORA ====");
    console.log("Horas: " + ahora.getHours());
    console.log("Minutos: " + ahora.getMinutes());
    console.log("Segundos: " + ahora.getSeconds());
    console.log("Milisegundos desde 1/1/1970: "+ ahora.getTime());
    console.log("milisegundos: " + ahora.getMilliseconds());
    ```

  - UTC

    ```javascript
    var ahora = new Date();
    console.log("Con UTC: ";
    console.log("==== FECHA ====");
    console.log("El año: " + ahora.getUTCFullYear()); // 4 digitos
    console.log("El mes: " + ahora.getUTCMonth()); // 0 - 11
    console.log("El día de la semana: " + ahora.getUTCDay()); // 0 - 6 (D - S)
    console.log("El día del mes: " + ahora.getUTCDate()); // 1-31
    console.log("==== HORA ====");
    console.log("Horas: " + ahora.getUTCHours());
    console.log("Minutos: " + ahora.getUTCMinutes());
    console.log("Segundos: " + ahora.getUTCSeconds());
    console.log("milisegundos: " + ahora.getUTCMilliseconds());
    ```

- Setters:
    - Local

    ```javascript
    var newYear = new Date(Date.UTC(2016, 1, 1));
    console.info("La fecha es " + newYear);
    
    newYear.setFullYear(1980); // Pasamos a 1980
    console.info("La fecha es " + newYear);
    
    newYear.setDate(56); // 1 Enero + 56 Días
    console.info("La fecha es " + newYear);
    
    newYear.setUTCMilliseconds(1500); // 1500ms en formato UTC
    console.info("La fecha es " + newYear);
    
    newYear.setUTCHours(36); // le sumamos 36 horas
    console.info("La fecha es " + newYear);
    
    newYear.setMonth(-6); // le quitamos 6 meses
    console.info("La fecha es " + newYear);
    ```

- Otros:
  - .getTimezoneOffset() *Devuelve la diferencia entre tu zona horaria y UTC (en minutos)*

    ```javascript
    ahora.getTimezoneOffset();
    ```

  - .toString(), .toDateString(), .toTimeString() *Devuelve una cadena con la fecha*

    ```javascript
    ahora.toString(); // Fecha y Hora
    ahora.toDateString(); // Solo Fecha
    ahora.toTimeString(); // Solo Hora
    ```

  - .toUTCString(), .toISOString() *Devuelve una cadena con la fecha en formatos específicos*

    ```javascript
    ahora.toISOString(); // ISO
    ahora.toUTCString(); // UTC
    ```

  - .toLocaleString() *Devuelve una cadena con la fecha en version local.*

    ```javascript
    var ahora = new Date();
    console.info(ahora.toLocaleString());
    
    // Código de idioma IETF para Alemán
    console.info(ahora.toLocaleString("de-DE"));
    
    // Opciones Avanzadas para fechas
    var opciones = { 
    weekday: 'long',
    year: 'numeric', 
    month: 'long', 
    day: 'numeric'};
    console.log(ahora.toLocaleString("de-DE", opciones));
    ```
  
  - Tiempo transcurrido:

    ```javascript
    var inicio = new Date();
    // + código
    var fin = new Date();
    var transcurso = fin.getTime() - inicio.getTime();
    console.info("Pasaron "+transcurso+"ms");
    ```


**Truco**

Usar getters para modificar fechas (días, meses, etc...)

Nota: Partiendo del ejemplo de [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/setDate)

- sin *getters*

  ```javascript
 	var theBigDay = new Date(1962, 6, 7);
 	theBigDay.toLocaleString(); // 6/7/1962 23:00:00
 	
 	var theBigDay = new Date(1962, 6, 7);
 	theBigDay.setDate(24);
 	theBigDay.toLocaleString() // 23/7/1962 23:00:00
 	
 	var theBigDay = new Date(1962, 6, 7);
 	theBigDay.setDate(32);
 	theBigDay.toLocaleString() // 31/7/1962 23:00:00
 	
 	var theBigDay = new Date(1962, 6, 7);
 	theBigDay.setDate(22);
 	theBigDay.toLocaleString() // 21/7/1962 23:00:00
 	
 	var theBigDay = new Date(1962, 6, 7);
 	theBigDay.setDate(22 + 32 +24);
 	theBigDay.toLocaleString() // 15/9/1962 23:00:00
 ```

- con *getters* 

  ```javascript
 	var theBigDay = new Date(1962, 6, 7);
 	theBigDay.toLocaleString(); // 6/7/1962 23:00:00
 	
 	var theBigDay = new Date(1962, 6, 7);
 	theBigDay.setDate(theBigDay.getDate() + 24);  
 	theBigDay.toLocaleString(); // 30/7/1962 23:00:00
 	
 	var theBigDay = new Date(1962, 6, 7);
 	theBigDay.setDate(theBigDay.getDate() + 32);
 	theBigDay.toLocaleString(); // 7/8/1962 23:00:00
 	
 	var theBigDay = new Date(1962, 6, 7);
 	theBigDay.setDate(theBigDay.getDate() + 22);
 	theBigDay.toLocaleString(); // 28/7/1962 23:00:00
 	
 	var theBigDay = new Date(1962, 6, 7);
 	theBigDay.setDate(theBigDay.getDate() + 22 + 32 + 24);
 	theBigDay.toLocaleString(); // 22/9/1962 23:00:00
  ```




### String

**Propiedades:**
- `.length` *Devuelve la longitud*:

  ```javascript
  var cadena = "Fictizia";
  
  console.log("Fictizia tiene " + cadena.length + " caracteres.");
  
  console.log("Una cadena vacia tiene " + ''.length + " caracteres.");
  ```
  
**Métodos:**

- `.fromCharCode()` *Devuelve una cadena creada mediante una secuencia [Unicode](https://www.wikiwand.com/es/Unicode)*:

  ```javascript
  console.info("Es es el año 2016 ("+ String.fromCharCode(8559,8559,8553,8548,8544) + ")");
  ```

- `.anchor()` *Crea un ancla HTML*:

  ```javascript
 	document.body.innerHTML = "Contenidos".anchor("contenidos"); 
 	// "<a name="contenidos">Contenidos</a>"
  ```

- `.link()` *Crea un enlace*:

  ```javascript
  var textoActivo="Nuestro Curso"
  var url="http://www.fictizia.com/formacion/curso_javascript"
  document.body.innerHTML = "Haga click para volver a " + textoActivo.link(url);
  ```

- `.charAt()` *Devuelve el carácter específico*:

  ```javascript
  var cadena="Fictizia";
  console.log("El carácter(posición) 3 es '" + cadena.charAt(3) + "'")
  ```

- `.charCodeAt()` *Devuelve el valor Unicode*:

  ```javascript
  var cadena="Fictizia";
  console.log("El carácter(posición) 3 es '" + cadena.charAt(3) + "', en unicode ("+cadena.charCodeAt(3)+")")
  ```


- `.concat()` *Combina el texto de dos o más cadenas*:

  ```javascript
  var cadena1 = "Oh ";
  var cadena2 = "qué maravillosa ";
  var cadena3 = "mañana'.";
  var combinacion = cadena1.concat(cadena2,cadena3);
  console.log(combinacion); // devuelve "Oh qué maravillosa mañana'."
  ```

- `.indexOf()` *Devuelve el índice o -1*:

  ```javascript
  "Mundo Web".indexOf("Web") // 6
  "Mundo Web".indexOf("web") // -1
  ```


- `.lastIndexOf()` *Devuelve el índice de la última coincidencia o -1*:

  ```javascript
  "Fictizia".lastIndexOf("i"); // 6
  "Fictizia".lastIndexOf("f"); // -1
  ```

- `.split()` *Divide una cadena usando un separador*:

  ```javascript
  var cadenaVerso = "Lorem Ipsum es simplemente el texto de relleno de las imprentas y archivos de texto. Lorem Ipsum ha sido el texto de relleno estándar de las industrias desde el año 1500";
  var cadenaMeses = "Jan,Feb,Mar,Apr,May,Jun,Jul,Aug,Sep,Oct,Nov,Dec";
  
  console.log(cadenaVerso.split(' '));
  console.log(cadenaMeses.split(','));
  ```

- [Using Slice(), Substring(), And Substr() In Javascript By Ben Nadel](https://www.bennadel.com/blog/2159-using-slice-substring-and-substr-in-javascript.htm)

- `.slice()` *Devuelve una cadena nueva con una sección de otra*:

  ```javascript
  var cadena = "Fictizia";
  console.log(cadena.slice(5)); // zia
  console.log(cadena.slice(0, 5)); // Ficti
  console.log(cadena.slice(3, -1)); // tizi
  ```

- `.substr()` *Devuelve los caracteres de una cadena comenzando en la localización especificada, y en el número de caracteres especificado.*:

  ```javascript
  var cadena = "Fictizia";
  console.log("(0,5): "    + cadena.substr(0,5)); // Ficti
  console.log("(5,3): "    + cadena.substr(5,3)); // zia
  ```

- `.substring()` *Devuelve un subconjunto*:

  ```javascript
  var cadena = "Fictizia";
  console.log("(0,5): "    + cadena.substring(0,5)); // Ficti
  ```

- `.toLocaleLowerCase()` *Devuelve todo en minúsculas con las características locales*:

  ```javascript
  console.log('FICTIZIA'.toLocaleLowerCase()); // 'fictizia'
  ```

- `.toLocaleUpperCase()`*Devuelve todo en mayúsculas con las características locales*:

  ```javascript
  console.log('fictizia'.toLocaleUpperCase()); // 'FICTIZIA'
  ```

- `.toLowerCase()` *Devuelve todo en minúsculas*:

  ```javascript
  console.log('FICTIZIA'.toLowerCase()); // 'fictizia'
  ```


- `.toUpperCase()` *Devuelve todo en mayúsculas*:

  ```javascript
  console.log('fictizia'.toUpperCase()); // 'FICTIZIA'
  ```

- `.trim()` *Elimina espacios vacios al principio y final de la cadena*:

  ```javascript
  console.log('  Fictizia '.trim()); // 'Fictizia'
  ```



### Arrays

- Creando un array:

  ```javascript
  var arreglo = [];
  arreglo = [1, "platano", "piscina", "manzana", true];
  ```

- Usando el Índice:

  ```javascript
  arreglo[1];
  ```

- Cambiar un valor del Índice:

  ```javascript
  arreglo[0] = "fresa";
  arreglo[4] = "pera";
  arreglo[2] = "limón";
  ```

- delete *sobrescribe a undefined*
    ```javascript
    delete arreglo[0];
    ```

- Elementos vacios:
    ```javascript
    arreglo[0] = undefined;
    ```

**Propiedades**

- Índice total:
    ```javascript
     arreglo.length;
    ```

- Usando el Índice total en un bucle:
    ```javascript
	var numeros = [1, 2, 3, 4, 5];
	for (var i = 0; i < numeros.length; i++) {
	  numeros[i] *= 10;
	}
    ```

**Métodos**

- `.isArray()` *Confirmar que se trata de un Array*:
    ```javascript
     var arreglo = [1,2,3]
     
     // true
     Array.isArray([1]);
     Array.isArray(arreglo);
     
     // false
     Array.isArray();
	    Array.isArray({});
	    Array.isArray(null);
	    Array.isArray(undefined);
    ```

- `.toLocalString()` *Retorna como string (configuración regional) todos los elementos*:
    ```javascript
	var numero = 1337.89;
	var fecha = new Date();
	var miArray = [numero, fecha, 'más datos'];
	
	var arrayConvertida = miArray.toLocaleString(); 
	console.log(arrayConvertida);     
    ```

- `.toString()` *Retorna una cadena de texto con todos los nombres*:
    ```javascript
	var amigos = ['Luis', 'Carlos', 'Marco', 'Eduardo'];
	console.log(amigos.toString());
    ```

- `.push()` *Añadir elemento al índice*:
    ```javascript
	arreglo.push("nuevo");
    ```

- `.pop()` *Eliminar el último elemento del índice*:
    ```javascript
     arreglo.pop();
    ```

- `.shift()` *Eliminar el primer elemento*:
    ```javascript
     arreglo.shift();
    ```

- `.unShift()` *Añade nuevos elementos al principio del array y devuelve la longitud actualizada*:
    ```javascript
	var miArray = [1, 2];
	
	miArray.unshift(true, "otros datos...");
	console.log(miArray);
    ```

- `.splice()` *Borrar*:
    ```javascript
     var manzana = arreglo.splice(3, 1);
    ```


- `.slice()` *Devuelve un nuevo Array con un segmento determinado del Array original*:
    ```javascript
	var frutas = ['Platano', 'Naranja', 'Limón', 'Manzana', 'Mango'];
	var citricos = frutas.slice(1, 3);
	console.info(citricos);
    ```

- `.concat()` *Retorna un nuevo Array con los Arrays especificados concatenados*:
   - Dos Arrays:
    ```javascript
     var arreglo = ['a', 2, true];
     var arreglo2 = [1, 2, 4];
    
     var nuevaArray = arreglo.concat(arreglo2);

	console.log(nuevaArray); 
    ```
   - Múltiples Arrays:
    ```javascript
     var arreglo = ['a', 2, true];
     var arreglo2 = [1, 2, 4];
     var otroArreglo = ['abc', 1, false]
    
     var nuevaArray = arreglo.concat(arreglo2, [5.25, 100], otroArreglo);

	console.log(nuevaArray);
    ```


- `.join()` *Une todos los elementos en una cadena*:
    ```javascript
	var array = ['dato1', 2, , 'masDatos'];
	var datosJuntos = array.join();    // 'dato1,2,masDatos'
	var datosJuntos2 = array.join('');    // 'dato12masDatos'
	var datosJuntos3 = array.join(' + '); // 'dato1 + 2 + masDatos'
    ```

- `.indexOf()` *Devuelve la posición donde se escuentra el elemnto o -1 si no lo encuentra*:
    ```javascript
	var array = [2, 5, 9];
	var index = array.indexOf(9); // 2
	var index = array.indexOf(12); // -1
    ```

- `.lastIdexOf()` *Devuelve la posición del último elemento que coincide o -1 si no lo encuentra*:
    ```javascript
	var array = [7, 1, 3, 7];
	array.lastIndexOf(7); // 3
	array.lastIndexOf(2); // -1
    ```

- `.sort()` *Ordenación de los elementos*:
    ```javascript
	var frutas = ['Platano', 'Naranja', 'Limón', 'Manzana', 'Mango'];
	frutas.sort(); // ["Limón", "Mango", "Manzana", "Naranja", "Platano"]
	
	var miArray = ['uno', 2, true, 'más datos...'];
	miArray.sort(); // [2, "más datos...", true, "uno"]
    ```

- `.reverse()` *Invierte el orden de un Array*:
    ```javascript
	var miArray = ['uno', 2, true, 'más datos...'];
	miArray.reverse(); 
	console.log(miArray) // ["más datos...", true, 2, "uno"]
    ```

- `.forEach()` *Se ejecuta la función por cada elemnto del array*:
    ```javascript
	function logger(element, index, array) {
	    console.log("array[" + index + "] = " + element);
	}
	[2, 5, 9].forEach(logger);
    ```

- `.map()`:
    ```javascript
	var arreglo = ["plátano", "fresa", "lima", "manzana"];
	var resultado = arreglo.map(function (elemento){return elemento + " modificado!"});
	console.log(resultado);
    ```

- `.some()` *Verifica si alguno de los elementos en el arreglo pasan la prueba implementada por la función dada:*:
    ```javascript
	function tamañoValido(elemento, indice, arrreglo) {
	  return elemento >= 10;
	}
	[12, 5, 8, 130, 44].some(tamañoValido);   // true
	[12, 54, 18, 130, 44].some(tamañoValido); // true
    ```


- `.every()` *verifica si todos los elementos en el arreglo pasan la prueba implementada por la función dada:*
    ```javascript
	function tamañoValido(elemento, indice, arrreglo) {
	  return elemento >= 10;
	}
	[12, 5, 8, 130, 44].every(tamañoValido);   // false
	[12, 54, 18, 130, 44].every(tamañoValido); // true    
    ```

- `.filter()` *Crea un nuevo array con aquellos elementos que cumplan la condición*:

  ```javascript
  function tamañoValido(elemento) {
    return elemento >= 10;
  }
  var filtrados = [true, 134, 10, 0, null, "Hola"].filter(tamañoValido);
  ```

- `.reduce()` *Aplica una función a un acumulador y a cada valor de un vector para reducirlo a un único valor (de izquierda a derecha)*:
  - Base:

  ```javascript
  var reduce = [0,-3,1,2,4,6].reduce(function(valorAnterior, valorActual, indiceActual, array){
    return valorAnterior + valorActual;
  });
  console.log(reduce); // 10
  ```
    
  - Sumar los valores de un Array:

  ```javascript
  var total = [0, 1, 2, 3].reduce(function(a, b){ return a + b; });
  ```

  - Fusionar varios Arrays en uno solo:

  ```javascript
  var integrado = [[0,1], [2,3], [4,5]].reduce(function(a,b) {
    return a.concat(b);
  });
  console.log("integrado es", integrado); //[0, 1, 2, 3, 4, 5]
  ```

- `.reduceRight()` *Aplica una función a un acumulador y a cada valor (de izq. a dcha.) de un vector para reducirlo a un único valor (de derecha a izquierda)*:

  ```javascript
  var reduceRight = [0,-3,1,2,4,6].reduce(function(valorAnterior, valorActual, indiceActual, array){
    return valorAnterior + valorActual;
  });
  console.log(reduceRight); // 10
  ```

**Arreglos avanzados**
```javascript
var arreglo1 = ["plátano", "fresa", "lima", "manzana"];
var arreglo2 = ["entrante", "primero", "segundo", "postre"];

var juntandoArreglos = [arreglo1, arreglo2];

function testArreglos () {
    console.log(juntandoArreglos[0][0]);
    console.log(juntandoArreglos[1][3]);
};
```

### Objetos

- [MDN Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)
- [w3schools Objects](http://www.w3schools.com/js/js_objects.asp)

**Objetos Literales**

- Propiedades:
    ```javascript
	var miObjeto = {
	    cadena: 'esto es una cadena',
	    numero: 2,
	    booleano: false
	};
	```


- Métodos:
    ```javascript
	var miObjeto = {
	    saludar: function(){
			console.log("hola!");
		}
	};
	```
	
- Trabajando con espacios y caracteres especiales:

  ```javascript
  var miObjeto = {
    nombre: "objeto",
    "año": 2015,
    "estado del sistema": "correcto"
  };
	
  console.log(miObjeto["año"]);
  miObjeto["estado del sistema"] = "fuera de servicio";
  console.log(miObjeto["estado del sistema"]);
  ```

- Acortar objetos:

  ```javascript
  var objetoAbreviado = objeto.muy.muy.largo.que.tiene.muchos["metodos y propiedades"];
  
  objetoAbreviado.propiedad1;
  objetoAbreviado.metodo1();
  ```

**Métodos**

- `.defineProperties()` *Define nuevas o modifica propiedades existentes directamente en el objeto, returnando el objeto.*:

  ```javascript
  var miObjeto = {propiedad: "Propiedad original..."}
  Object.defineProperties(miObjeto, {
    "propiedad1": {
    value: true,
    writable: true
    },
    "propiedad2": {
    value: "Cadena de texto",
    writable: false
    }
  });
  console.info(miObjeto);
  miObjeto.propiedad = "Propiedad original Modificada";
  console.info(miObjeto.propiedad);
  miObjeto.propiedad2 = "Cadena de texto... ¿modificada?";
  console.info(miObjeto.propiedad2);
  ```

- `.getOwnPropertyDescriptor()` *Devuelve las detalles de los objetos y métodos del objeto. Undefined en caso de no existir*:

  ```javascript
  var miObjeto = {
    metodo: function() {
    console.log(miObjeto.propiedad1)
    },
    propiedad1: "Datos"
  };
 
  console.info(Object.getOwnPropertyDescriptor(miObjeto, 'propiedad1'));
  // Object {value: "Datos", writable: true, enumerable: true, configurable: true}
  
  console.info(Object.getOwnPropertyDescriptor(miObjeto, 'inventado'));
  // undefined
  ```

- `.getOwnPropertyNames()` *Devuelve un array con todos los nombres de las propiedades y métodos del objeto*:

  ```javascript
  var miObjeto = {
    metodo: function() {
    console.log(miObjeto.propiedad1)
    },
    propiedad1: "Datos"
  };
  
  console.log(Object.getOwnPropertyNames(miObjeto));
  // ["metodo", "propiedad1"]
  ```

- `.isExtensible()` *Determina si un objeto es extensible*:

  ```javascript
  var miObjeto = {
    metodo: function() {
    console.log(miObjeto.propiedad1)
    },
    propiedad1: "Datos"
  };
  
  console.log("¿Se puede extender?", Object.isExtensible(miObjeto));
  
  var sellado = Object.seal(miObjeto);
  console.log("¿Se puede extender?", Object.isExtensible(sellado));
  
  var congelado = Object.freeze(miObjeto);
  console.log("¿Se puede extender?", Object.isExtensible(congelado));
  
  Object.preventExtensions(miObjeto);
  console.log("¿Se puede extender?", Object.isExtensible(miObjeto));
  ```


- `.hasOwnProperty()` *Devuelve true o false si l apropiedad existe o no*:

  ```javascript
  var miObjeto = {
    metodo: function() {
     console.log(miObjeto.propiedad1)
    },
    propiedad1: "Datos"
  };
  
  console.log("¿Tiene la propiedad \"propiedad1\"?", miObjeto.hasOwnProperty('propiedad1'));
  console.log("¿Tiene la propiedad \"propiedad2\"?", miObjeto.hasOwnProperty('propiedad2'));
  ```


- `.propertyIsEnumerable()` *Devuelve true o false si la propiedad es especificada es enumerable.*:

  ```javascript
  var miObjeto = {
    metodo: function() {
     console.log(miObjeto.propiedad1)
    },
    propiedad1: "Datos"
  };
  
  console.log("¿Es enumerable \"propiedad1\"?", miObjeto.propertyIsEnumerable('propiedad1'));
  console.log("¿Es enumerable \"metodo\"?", miObjeto.propertyIsEnumerable('propiedad2'));
  ```

- `.toLocaleString()` *Retorna como string (configuración regional) todas las propiedades*:

  ```javascript
  var fecha = new Date();
  
  var miObjeto = {
    metodo: function() {
     console.log(miObjeto.propiedad1)
    },
    propiedad1: "Datos",
    fecha: fecha
  };
  
  miObjeto.toLocaleString()
  console.log("La fecha es ", miObjeto.fecha);
  ```

### Funciones


- Propiedad *name*:

  ```javascript
  function miFuncion (){
    // vacia
  };

  console.log(miFuncion.name);
  ```


- **Declaración y ejecución**:

  ```javascript
  function dameTrue (){
    return true
  };

  function dameFalse () {
    return false
  };

  dameTrue();
  dameFalse();
  ```

- **this**:
  - como función (*this* contexto *window*)

    ```javascript
    function ambitoGlobal () {
    return this;
    }
    
    ambitoGlobal()
    ```

  - como método en un objeto (*this* contexto objeto al que pertenece el método)

    ```javascript
    var objeto = {};
    
    objeto.miMetodo = function () {
    return this;
    }
    
    objeto.miMetodo();
    ``` 

  - como constructor de un objeto (*this* contexto objeto creado)
  - `.apply()` y `.call()` (modificación explícita de *this*)

    ```javascript
    var perro1 = {
    raza: 'Mastín',
    getRaza: function() {
      return this.raza;
    }
    };
    var perro2 = { raza: 'Golden' };

    console.log(perro1.getRaza.call(perro2));
    ```

- **Argumentos:**
  - El exceso de argumentos no es un problema
  - La falta de argumento crea un valor indefinido
    - El Objeto Arguments no es un Array, solo es similar.

    ```javascript    
    function pruebaArguemntos () {
      console.log(arguments);
      console.info(arguments[0]);
      console.info(arguments[1]);
    }
     
    pruebaArgumentos (1, "vale", true);
    ```

- [Objeto Arguments](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Funciones/arguments)


- **Retorno**

  ```javascript
  function sumaCuadrados (a, b) {
    return (a*a) + (b*b);
  };
  ```

### Scope

- Declaración y ejecución:

  ```javascript
  var numero = 450;
  var otroNumero = 23;

  function sumaCuadrados (a, b) {
    var numero = a;
    var otroNumero = b;
    var calculo = (numero*numero) + (otroNumero*otroNumero);
    console.log("\"numero\" es \""+numero+"\", local");
    console.log("\"otroNumero\" es \""+otroNumero+"\", local");
  };

  function verificarGlobales() {
    console.log("\"numero\" es \""+numero+"\", global");
    console.log("\"otroNumero\" es \""+otroNumero+"\", global");
  };
  ```

### Funciones Avanzadas

- Anónimas (expresiones):

  ```javascript
  var sumaCuadrados = function (a, b) {
    return (a*a) + (b*b);
  };
  
  console.log("El .name de sumaCuadrados es "+sumaCuadrados.name)
  ```

- Funciones como dato:

  ```javascript
  function saludo () {
    console.log("hola!");
  };

  function lanzar (funcion){
    funcion();
  };
  ```

- Funciones anónimas autoejecutables:

  ```javascript
  (function() {
    console.log("hola Amigo/a")
  }) (); //ex:Jquery
  ```


- Funciones anónimas con parámetros:

  ```javascript
  ( function(quien){
     console.log("hola " + quien);
  })("Amigo/a");
  ```


- Función que devuelve una función anónima:
  - Asignando una variable:

    ```javascript
    function saludo(quien){
    return function(){
      alert("hola " + quien);
    }
    }
    var saluda = saludo("Amigo/a");
    saluda();
    ```

  - Sin asignar una variable:

    ```javascript
    function saludo(quien){
    return function(){
      alert("hola " + quien);
    }
    }
    saludo("Amigo/a")();
    ```


### Funciones Avanzadas: Anidación

- Con variables:

  ```javascript
  function saludar(quien){
    function alertasaludo(){
    console.log("hola " +  quien);
    }
    return alertasaludo;
  }
  var saluda = saludar("Amigo/a");
  saluda();
  ```

- Ejecución directa:

  ```javascript
  function saludar(quien){
    function alertasaludo(){
    console.log("hola " +  quien);
    }
    return alertasaludo;
  }
  saludar("Amigo/a")();
  ```
    
### Funciones Avanzadas: Recursión

- Calcular el [factorial](https://www.wikiwand.com/es/Factorial).

  ```javascript
  function factorial(n){
    return n <= 1 ? 1 : n * factorial(n-1);
  }
  
  factorial(0); // n! = 1
  factorial(1); // n! = 1
  factorial(2); // n! = 2
  factorial(3); // n! = 6 (3*2*1)
  factorial(4); // n! = 24 (4*3*2*1)
  factorial(5); // n! = 120 (5*4*3*2*1)
  factorial(6); // n! = 720 (...)
  // ...
  ```

### Funciones Avanzadas: Closures

> Los closures son funciones que manejan variables independientes. En otras palabras, la función definida en el closure "recuerda" el entorno en el que se ha creado.

> No es aconsejable crear innecesariamente funciones dentro de otras funciones si no se necesitan los closures para una tarea particular ya que afectará negativamente el rendimiento del script tanto en consumo de memoria como en velocidad de procesamiento.
> [Closures MDN](https://developer.mozilla.org/es/docs/Web/JavaScript/Closures)

- Fábrica de función:

  ```javascript
  function sumador(x) {
    return function(y) {
    return x + y;
    };
  }

  var sum1 = sumador(10); //Closure
  var sum2 = sumador(30); //Closure

  console.log(sum1(2)); // Devuelve 12
  console.log(sum2(2)); // Devuelve 32
  console.log(sumador(20)(2)); //Devuelve 22
  ```

- Otro ejemplo, ahora temporizado:

  ```javascript
  function saludar(segundos){
    var hola = "Hola, Hola!";

    setTimeout(function(){
    console.info(hola);
    }, segundos * 1000);
  }

  saludar(2);
  ```

- Otro ejemplo... más útil:

  ```javascript
  var varGlobal = "Soy un dato Global";
  var burbuja;

  function nivel1() {
    var varInterna = "Soy un dato interno. -> nivel1";

    function nivel2() {
    console.log("Estoy dentro de la funcion -> nivel2")
    console.log("Estoy dentro de la funcion -> nivel2 y puedo acceder al nivel1: "+varInterna)
    }

    burbuja = nivel2;

  }

  nivel1();

  burbuja();
  console.log("Burbuja recuerda su contexto original")
  ```

### Funciones Avanzadas: Callbacks

> En programación de computadoras, una devolución de llamada o retrollamada (en inglés: callback) es una función "A" que se usa como argumento de otra función "B". Cuando se llama a "B", ésta ejecuta "A". Para conseguirlo, usualmente lo que se pasa a "B" es el puntero a "A".
> [Callbacks en Wikiwand](https://www.wikiwand.com/es/Callback_(inform%C3%A1tica))

- Ejemplo condensado:

  ```javascript
  var quieroCallback = function(parametro, callback){
    if ((callback) && (typeof callback === 'function')){
      callback(parametro);
    } else {
    console.log(parametro, callback);
    }
  }
 
  quieroCallback('a', 'b');
 
  quieroCallback('a', function(val){
    console.log(val);
  });
  ```


- Ejemplo con Jquery:

  ```javascript
  $('#elemento').fadeIn('slow', function() {
    // código del callback
  });
  ```


- Otro ejemplo:

  ```javascript
  function comerSandwich(elemento1, elemento2, callback) {
    console.info('ñam ñam... empiezo con el sándwich.\n\nMe gusta porque tiene tiene ' + elemento1 + ', ' + elemento2);
    callback();
  }

  comerSandwich('jamón', 'queso', function() {
    console.info('Ya terminé...');
  });
  ```


- Ejemplo con Callback opcional:

  ```javascript
  function comerSandwich(elemento1, elemento2, callback) {
    console.info('ñam ñam... empiezo con el sándwich.\n\nMe gusta porque tiene tiene ' + elemento1 + ', ' + elemento2);
    
    if (callback) {
      callback();
    }
  }

  comerSandwich('jamón', 'queso');
  ```


- Sanitizar el Callback:

  ```javascript
  function comerSandwich(elemento1, elemento2, callback) {
    console.info('ñam ñam... empiezo con el sándwich.\n\nMe gusta porque tiene tiene ' + elemento1 + ', ' + elemento2);
    
    if (callback && typeof(callback) === "function") {
      callback();
    }
  }

  comerSandwich('jamón', 'queso');
  ```


### Funciones Avanzadas: Asincronia

```javascript
function comerSandwich(elemento1, elemento2, callback) {
  console.info('ñam ñam... empiezo con el sándwich.\n\nMe gusta porque tiene tiene ' + elemento1 + ', ' + elemento2);
	    
  setTimeout(function alarma(){
    console.log("ring! ring!.. pasaron los 5 segundos!");
  }, 5000);
	    
  if (callback && typeof(callback) === "function") {
    callback();
  }
}
	
comerSandwich('jamón', 'queso', function() { 
  console.log('Ya terminé...');
});
```


- Más información: 
  - [Callback Functions in JavaScript de Louis Lazaris](http://www.impressivewebs.com/callback-functions-javascript/)
  - [Creando y utilizando callbacks de Pablo Novas en fernetjs](https://fernetjs.com/2011/12/creando-y-utilizando-callbacks/)

### Funciones Avanzadas: Funciones anónimas autoejecutadas

- **Sintaxis:**

  ```javascript
    (function(){
      console.log('Hola Mundo!');
    })();
  ```

- **Incluyendo referencias y manipulando otros elementos:**

  ```javascript
  var myApp = myApp || {};
    
  (function(w, doc, ns){
    ns.accesoWindow = function(){
    return w === window;
    };
    ns.accesoDocument = function(){
    return doc === document;
    };
    ns.confirmacion = function(){
    console.log('Hola Mundo! Mis caracteristicas son: \n Acceso a Window: '+this.accesoWindow()+'\n Acceso a Document: '+this.accesoDocument());
    }
  })(window, document, myApp);
  
  // myApp.confirmacion()
  ```


### Promesas

![promises_ecma6](../assets/promises.png)

> A promise represents the eventual result of an asynchronous operation. The primary way of interacting with a promise is through its *then* method, which registers callbacks to receive either a promise’s eventual value or the reason why the promise cannot be fulfilled.
> From [promisesaplus.com](http://promisesaplus.com/)

- Estados:
    - **Fulfilled** – La acción en relación con la promesa se logró.
    - **Rejected** – La acción en relación con la promesa falló.
    - **Pending** – Pendiente, no se ha cumplido o rechazado aún.
    - **Settled** - Reiterada, se ha cumplido o se ha rechazado.

**En ECMA6**:
- [Soporte en navegadores](http://caniuse.com/#search=promise)  

**Una promesa**:

```javascript
var cuentaPromesas = 0;
var errorMode = false;

function testPromesa() {
  var numPromesaActual = ++cuentaPromesas;
		
  console.warn("Promesa Asíncrona numero ("+numPromesaActual+") - Iniciada")
		
  var miPromesa = new Promise(function(resolve, reject) {     
    console.info("Promesa Asíncrona numero ("+numPromesaActual+") - Proceso asincrónico empezado");
		    
    if(errorMode){
    reject(numPromesaActual)
    } else {
    window.setTimeout(function() {
      resolve(numPromesaActual)
    }, Math.random() * 2000 + 1000);
    }
  });
  
  miPromesa.then(function(val) {
    console.info("Promesa Asíncrona numero ("+val+") - Proceso asincrónico terminado");
    console.warn("Promesa Asíncrona numero ("+numPromesaActual+") - Finalizada");
  }).catch(function(val){
    console.error("Promesa Asíncrona numero ("+val+") - ERROR FATAL");
  });
}

testPromesa();
```

**Usando `.race()`**

```javascript	
var p1 = new Promise(function(resolve, reject) { 
  setTimeout(resolve, 500, "uno"); 
});
var p2 = new Promise(function(resolve, reject) { 
  setTimeout(resolve, 100, "dos"); 
});
		
Promise.race([p1, p2]).then(function(value) {
  console.log(value); // "dos" - p2 más rápida
}); 
```	

**Usando `.all()`**

```javascript
var errorMode = false;
	
var p1 = new Promise(function(resolve, reject) {
  console.log("P1 - Iniciada"); 
  setTimeout(resolve, 1000, "P1 - Terminada"); 
}); 
var p2 = new Promise(function(resolve, reject) {
  console.log("P2 - Iniciada");
  setTimeout(resolve, 2000, "P2 - Terminada"); 
});
var p3 = new Promise(function(resolve, reject) {
  if(errorMode){
    reject("errorMode-Activado");
  } else {
    console.log("P3 - Iniciada");
    setTimeout(resolve, 3000, "P3 - Terminada");
  }
});
var p4 = new Promise(function(resolve, reject) {
  console.log("P4 - Iniciada");
  setTimeout(resolve, 4000, "P4 - Terminada");
});
		
Promise.all([p1, p2, p3, p4]).then(function(value) { 
  console.info("Promise.all -> TODO TERMINADO", value)
}, function(reason) {
  console.log("Parece... que fallamos!", reason)
});
```

**Alternativas para usar promesas**:
- [Q](https://github.com/kriskowal/q) (muy utilizada en Nodejs)
- [Q Docs](https://github.com/kriskowal/q/wiki/API-Reference)

  ```javascript
  function primeraFuncion() {
    var deferred = Q.defer();
    setTimeout(function() {
    console.info('Primera funcion');
    deferred.resolve();
    }, 2000);
    return deferred.promise;
  }
   		
  function segundaFuncion() {
    var deferred = Q.defer();
    setTimeout(function() {
    console.info('Segunda funcion');
    deferred.resolve();
    }, 1000);
    return deferred.promise;
  }
  
  Q()
    .then(primeraFuncion)
    .then(segundaFuncion)
    .done();		
  ```

- [RSVP.js](https://github.com/tildeio/rsvp.js)
- [When.js](https://github.com/cujojs/when)

### Prototipo

En lo que a herencia se refiere, JavaScript sólo tiene una estructura: objetos. Cada objeto tiene una propiedad privada (referida como su `[[Prototype]]`) que mantiene un enlace a otro objeto llamado su prototipo. Ese objeto prototipo tiene su propio prototipo, y así sucesivamente hasta que se alcanza un objeto cuyo prototipo es `null`. Por definición, `null` no tiene prototipo, y actúa como el enlace final de esta cadena de prototipos.

```javascript
function Vehicle(maxSpeed) {
    this.maxSpeed = maxSpeed;
}

Vehicle.prototype.getMaxSpeed = function() {
    return this.maxSpeed;
}

function Car(maxSpeed) {
    Vehicle.call(this, maxSpeed);
}

Car.prototype = new Vehicle();
```
