# 📘 Notas de libro: Javascript - The Definitive Guide (7ma edición)

## 2.2) Comments
Los comentarios en JavaScript se escriben de la siguiente manera:

```js
/* Text */

// Text

/* 
 * Text
 *
 */
```

---

## 2.3) Literals
Son los valores que aparecen directamente en el programa.

---

## 2.4) Identifiers and Reserved Words

### Identifiers
Los nombres de las variables pueden empezar con:
- Letras
- Guion bajo (`_`)
- Símbolo de dólar (`$`)

❌ Los números **no están permitidos** al inicio del nombre de una variable:  

```js
let 3prueba = 3; // Inválido
```

---

### 2.4.1) Reserved Words
Evitar usar las siguientes palabras para variables, constantes, etc:

```
as | const | export | get | null | target | void
async | continue | extends | if | of | this | while
await | debugger | false | import | return | throw | with
break | default | finally | in | set | true | yield
case | delete | for | instanceof | static | try
catch | do | from | let | super | typeof
class | else | function | new | switch | var
enum | implements | interface | package | private | protected | public
arguments | eval
```

---

## 2.5) Unicode
En JavaScript se puede usar Unicode para nombrar variables con caracteres distintos a letras latinas.  
Ejemplo:  

```js
let π = 3.1416;
```

### 2.5.1) Unicode Escape Sequences
Se pueden usar secuencias de escape Unicode:

```js
let café = 5;
caf\u00e9
caf\u{E9}
```

### 2.5.2) Unicode Normalization
⚠️ Precaución: Cuando se trabaja con caracteres **no ASCII**, puede haber problemas de normalización:  
- Ejemplo: `é` puede lucir igual, pero tener diferentes códigos Unicode.  
- Esto puede generar variables diferentes aunque parezcan idénticas.  

👉 Recomendación: **evitar caracteres no ASCII en identificadores.**

---

# 📖 Chapter 3: Types, Values, and Variables

## 3.1) Overview and Definitions
Las categorías de tipos de datos en JS son:
- **Primitivos (inmutables)**
  - `number`
  - `string` (⚠️ inmutable)
  - `boolean`
  - `null` (sin métodos)
  - `undefined` (sin métodos)
  - `symbol`
- **Objetos (mutables)**
  - Colección de propiedades (`name: value`)  
  - Sin orden específico

### Estructuras
- **Arrays** → Colección ordenada de datos.  
- **Set** → Conjunto de valores únicos.  
- **Map** → Mapeo clave → valor.  

### Notas
- JS cuenta con **Garbage Collection** para memoria.  
- Los **objetos son mutables**, los **primitivos inmutables**.  
- Constantes → `const`  
- Variables → `let`  
- Comparaciones → usar `===` (estricta).  

---

## 3.2) Numbers
- Representan enteros y números reales aproximados.  
- Son de **64 bits flotante** (IEEE 754, tipo *double*).  
- Rango aproximado:
  - Reales: ±1.7976931348623157 × 10^308  
  - Enteros exactos: −2^53 a 2^53  

👉 Usar fuera de este rango puede producir **pérdida de precisión**.  

---

### 3.2.1) Integer Literals
- **Decimal**: normal (`123`).  
- **Hexadecimal**: prefijo `0x` o `0X`.  
- **Binario**: prefijo `0b`.  
- **Octal**: prefijo `0o`.  

---

### 3.2.2) Floating-Point Literals
Un número real contiene un punto decimal:  

```js
3.23
6.23e23 // = 6.23 × 10^23
1.42E-32 // = 1.42 × 10^-32
```

---

### 3.2.3) Arithmetic in JavaScript
Operadores:
```js
+   // suma
-   // resta
*   // multiplicación
/   // división
%   // módulo
**  // potencia
```

Funciones avanzadas → `Math`  

#### Errores posibles
- `Infinity` → resultado demasiado grande.  
- `-Infinity` → resultado demasiado grande negativo.  
- **Underflow** → número cercano a `0` (ej. `-0`).  
- **NaN (Not a Number)** →  
  - `Infinity / Infinity`  
  - `Math.sqrt(-1)`  
  - `"hola" / 34`  

#### Representaciones
```js
Number.POSITIVE_INFINITY
Number.NEGATIVE_INFINITY
Number.NaN
```

👉 `NaN` no es igual ni a sí mismo. Usar:  
```js
Number.isNaN(x)
Number.isFinite(x)
```

#### Zero y -Zero
```js
let zero = 0;
let negz = -0;

zero === negz       // true
1/zero === 1/negz   // false (Infinity vs -Infinity)
```

---

### 3.2.4) Binary Floating-Point and Rounding Errors
JS usa aproximaciones en operaciones decimales → cuidado con comparaciones de igualdad.

---

### 3.2.5) BigInt (Arbitrary Precision Integers)
Introducido en **ES2020**.  
Permite enteros muy grandes (no enfocado en criptografía).  

```js
123n
34n
BigInt(2323)
```

⚠️ Reglas:
- Solo operaciones entre **BigInt y BigInt**.  
- Comparación estricta distingue tipo:  
  ```js
  0 == 0n   // true
  0 === 0n  // false
  ```

---

### 3.2.6) Dates and Times
JS soporta fechas y tiempos con `Date`.  

```js
Date.now()
new Date()
date.getTime()
```

Internamente se manejan como **timestamps**.

---

## 3.3) Text

- **Strings** son **inmutables**.  
- Cada carácter se representa con unidades de 16 bits.  
- Se puede iterar con loops.  

### 3.3.1) String Literals
📌 (Sección incompleta en el apunte original, aquí se pueden agregar ejemplos de comillas simples, dobles y backticks).