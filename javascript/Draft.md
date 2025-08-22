Notas: 21/08/25

2.2) Comments:
Los comentarios se escriben de esta manera
/* Text */

// Text

/* 
 * Text
 *
 */

 2.3) Literals
 Son los valores que aparecen directamente en el programa

 2.4) Identifiers and Reserved Words
 Los nombres de las variables pueden empezar con:
 - letras
 - guion bajo (_)
 - simbolo de dolar ($)

 Los numeros no estan permitidos para que inicie el nombre de una variables (ej: let 3prueba = 3;)


2.4.1) Reserved words:
Evitar usar las siguientes palabras para llamar variables, constantes, etc:

as | const | export | get | null | target | void |
async | continue | extends | if | of | this | while |
await | debugger | false | import | return | throw | with |
break | default | finally | in | set | true | yield |
case | delete | for | instanceof | static | try |
catch | do | from | let | super | typeof |
class | else | function | new | switch | var |
enum | implements | interface | package | private | protected | public |
arguments | eval |

2.5) Unicode
En javascript se puede usar para llamar caracteres a otros caracteres diferente a letras: π 

2.5.1) Unicode Escape Sequences
Se puede usar caracteres de escape para referirse a una misma variable. Ejemplo:

let café = 5;
caf\u00e9
caf\u{E9}


2.5.2) Unicode Normalization
Tener en cuenta que cuando se trabaja con caracteres No ASCII, puede tener problemas porque en Unicode un caracteres puede lucir igual (ej: é), pero puede tener diferentes Unicode, y hacer referencia a diferentes variables que no son visibles desde la pantalla o editor de texto.
- De preferencia, no utilizar NO-Ascii caracteres.


Chapter 3: Types, Values, and Variables
3.1) Overview and Definitions
Las categorias de tipos de datos que hay son:
- primitivos
- objetos

los tipos de datos primitivos son (immutables):
- numbers
- strings <= ojo: es immutable
- boolean
- null (no tienen metodos)
- undefined (no tienen metodos)
- symbol

objetos:
 Es una coleccion de "properties". Cada propiedad tiene un "name" y un "value" (puede ser un valor primitivo u otro objeto) 
 Es una collección sin orden

arrays:
 Es un coleccion ordenada de datos

set:
 Representa un conjunto de valores

map:
 Representa un mapeo de una "key" y su "value"


JS tiene un Garbage Collection de gestion de memoria.

Los objetos son "mutable" (puede cambiar sus valoers de las propiedades o del array) y los tipos primitivos son "immutable" (sus valores no cambia).

Las constantes son declaradas como "const"
Las variables son declaradas como "let"

Se debe usar "===" para la igualdad (el "==" hace un inferencia de la igualdad, es decir, lo interpreta al modo de JS)

3.2) Numbers

Sirve para representar "enteros" y aproximar numeros "reales"
Tienen una capacidad de 64bits flotante (en otros lenguajes se les dice "double" ).
Es decir que puede escribir decimales desde desde ±1.7976931348623157 × 10^308 y pequeños como ±5 × 10^−324.

Por otro lado, los enteros, puede tomarlos desde:
−9,007,199,254,740,992 (−2^53) hasta 9,007,199,254,740,992 (2^53)

Si usas enteros fuera de estos limites, puede que pierdas precisión.
Numerical Literal se les dice a los numeros que se muestran directamente.

3.2.1) Integer literals

Los Literal en JS estan en base 10.
Para usar hexadecimales se usa "0x" o "0X" al inicio, luego del numero hexadecimal.
Si quieres usar binario, usa el prefijo "0b" 
Si quieres usar octal, usa el prefijo "0o"

3.2.2) Floating-pont literals
Un numero real es aquel que tiene un punto decimal (ej: 3.23)
tambien se puede expresar numeros reales asi:
(la "e" o "E" significa multiplicado por 10 y elevado a la "n")
6.23e23
1.42E-32

3.2.3) Arithmetic in JavaScript
Operadores disponibles:
+, -, /, *, % (modulo: es el resto de una division), ** (representa la potencia)
Para mas funciones complejas, JS tiene el objeto "Math"

Hay posibles errores que puedes presentar:
  Infinity (cuando el numero resultante es mas grande de la capacidad del tipo de dato)
  - Infinity (igual que el anterior pero en negativo)

Tambien se tiene el "Underflow", que es cuando el numero resultante esta muy cerca a "0" y lo mismo, pero en negativo (a esto se le llama "negative zero", no es indistinguible desde del 0 normal)

Puedes obtener el valor infitivo de la siguiente forma:
- si divides 0 entre 0

Puedes obtener como resultado "NaN" (Not a Number) si haces lo siguiente:
- Si divides Infinity entre Infinity
- Le haces Raiz cuadrada a un numero negativo
- Usas operadores aritmeticos para valores no numericos y no pueden convertirse a numero ("hola"/34)

Otras maneras de escribir "Infinity" y "NaN":
- Number.POSITIVE_INFINITY
- Number.NEGATIVE_INFINITY
- Number.NaN

Una caracteristica de "NaN" no se le puede comparar con una igual (Ej. x === NaN  o  Number.isNaN(x) )

En su lugar, puedes usar "Number.isFinite()" que indica si es un numero, diferente a NaN, Infinity o -Infinity.

Puedes hacer diferencia de un zero regular y un negative zero, de la siguiente forma:

let zero = 0; // Regular zero
let negz = -0; // Negative zero
zero === negz // => true: zero and negative zero are equal
1/zero === 1/negz // => false: Infinity and -Infinity are not equal

3.2.4) Binary Floating-Point and Rounding Errors

JS maneja en sus operaciones aproximaciones para llegar a los numeros decimales, por lo que se debe tener cuidado de hacer aritmetica con esta asginaciones de valores, en especial, hacer igualdades con ellos (porque son inprecisas)

3.2.5) Arbitrary Precision Integers with BigInt

En ES2020, salio un tipo de dato numero llamado "BigInt" que tiene una capacidad gigante para numeros enteros. No esta enfocado a la cryptografia.
Por defecto los BigInt utiliza la base 10.
Se escribe de la sigueinte forma:

123n
34n

Puedes convertir un enteros de JS a BigInt asi:
BigInt(2323)

Los bigtint Trabaja con operaciones aritmetica entre otros numeros BigInt.
Saldra error si tu haces una operacion aritmetica de BigInt con un numero regular de JS, ejemplo:
233n*3

Lo que no genera problemas es los operadores de comparación como:
1n < 2 //true
5n > 10 //false
0 == 0n //true
0 === 0n //falso, porque esta igualdad tambien compara el tipo de dato


3.2.6) Dates and Times
JS tambien puede usar fechas y horas. 
- Date.now()
- new Date()
- now.getTime()

Tambien se tiene una representación como "timestamp".

3.3) Text

Los String son immutable.
Cada caracter de un string tiene 16bits contenidos.
Se puede iterar con un loop.

3.3.1) String Literals

Se puede usar los simbolos ' , " y `, para representar los strings.
Cuando se quiere contener valores "enclose" para hacer una oración:
`"Ella dijo 'hola'", el dijo``

Para usar el single quote dentro de un string de single quotes, puede usar el escape \'