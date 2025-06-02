# 02. Variables y Tipos de Datos en PHP

---

## 1. ¿Qué es una variable?

Una **variable** es un espacio de memoria donde puedes guardar un valor para usarlo más adelante en tu programa. Las variables permiten almacenar datos que pueden cambiar durante la ejecución del script. En PHP, todas las variables empiezan con el símbolo **\$** seguido del nombre de la variable.

---

## 2. Reglas para nombrar variables en PHP

* Siempre empiezan por **\$** (ejemplo: `$nombre`).
* El primer carácter después de `$` debe ser una **letra** o un **guion bajo** (`_`).
* El resto pueden ser letras, números o guion bajo.
* **No** pueden tener espacios, tildes, eñes ni caracteres especiales.
* Son **case-sensitive**: `$edad` y `$Edad` son diferentes variables.

**Ejemplos válidos:**

```php
$nombre;
$_usuario1;
$precio_total;
```

**Ejemplos inválidos:**

```php
$1usuario;         // Empieza por número
$nombre completo;  // Tiene espacio
$nombre-completo;  // Tiene guion
```

---

## 3. Asignación de valores a variables

Para asignar un valor a una variable se usa el signo igual (`=`):

```php
$edad = 20;
$nombre = "Arnau";
```

Puedes cambiar el valor cuando quieras:

```php
$edad = 25;
```

---

## 4. Tipos de datos principales en PHP

En PHP no hace falta declarar el tipo de dato, se asigna automáticamente según el valor que le des a la variable. Los tipos más usados son:

### 4.1 String (cadena de texto)

Se escriben entre comillas dobles o simples:

```php
$texto = "Hola";
$mensaje = 'Mundo';
```

### 4.2 Integer (número entero)

Números sin decimales:

```php
$edad = 18;
$contador = -5;
```

### 4.3 Float o Double (número decimal)

Números con decimales:

```php
$precio = 3.50;
$pi = 3.1416;
```

### 4.4 Boolean (verdadero o falso)

Solo puede ser `true` (verdadero) o `false` (falso):

```php
$es_mayor = true;
$aprobado = false;
```

### 4.5 Null (sin valor)

Representa una variable sin valor asignado:

```php
$variable = null;
```

---

## 5. Cómo saber el tipo de una variable

Puedes usar la función `gettype()` o `var_dump()` para saber el tipo y valor de una variable:

```php
$edad = 20;
var_dump($edad);      // int(20)
echo gettype($edad);  // integer
```

---

## 6. Conversión de tipos (casting)

Puedes convertir el tipo de una variable usando el “cast”:

```php
$numero = "100";        // string
$numero = (int)$numero;  // integer
```

Otros ejemplos:

```php
$decimal = 7.99;
$entero = (int)$decimal;     // 7
$texto = (string)$entero;    // "7"
$booleano = (bool)$entero;   // true
```

---

## 7. Constantes

Las **constantes** almacenan valores que no cambian durante la ejecución del programa. En PHP se pueden declarar de dos maneras principales:

### 7.1 Usando `define()`

* No lleva el signo `$`.
* Se recomienda usar el nombre en mayúsculas por convención.

```php
define("PI", 3.1416);
echo PI;    // 3.1416
```

* Se puede usar en cualquier parte del código, incluso dentro de funciones.

### 7.2 Usando `const`

* Se utiliza en el ámbito global (fuera de funciones) o dentro de clases.
* Sintaxis más moderna, común en programación orientada a objetos.

```php
const IVA = 0.21;
echo IVA;   // 0.21
```

* Dentro de una clase:

```php
class Ejemplo {
    const MENSAJE = "Hola";
}
echo Ejemplo::MENSAJE;
```

**Diferencias principales:**

* `define()` permite nombres dinámicos y se puede usar en cualquier parte del código.
* `const` solo puede usarse en el ámbito global o dentro de clases, y el nombre debe ser literal (no variable).

Una vez definida una constante, **no puedes cambiar su valor**.

---

## 8. Errores comunes con variables

* Olvidar el `$` al declarar o usar la variable.
* Usar caracteres inválidos en el nombre.
* Confundir mayúsculas y minúsculas.
* Reasignar sin querer una constante.

---

## 9. Ejemplo práctico

```php
<?php
    $nombre = "Arnau";
    $edad = 20;
    $precio = 19.95;
    $aprobado = true;
    $nulo = null;

    echo "Nombre: $nombre<br>";
    echo "Edad: $edad<br>";
    echo "Precio: $precio<br>";
    echo "¿Aprobado?: $aprobado<br>";
    echo "Valor nulo: $nulo<br>"; // No muestra nada
    var_dump($aprobado);  // bool(true)
?>
```

---

## 10. Recursos para practicar y aprender más

* [PHP Variables - W3Schools](https://www.w3schools.com/php/php_variables.asp)
* [PHP Manual - Tipos de datos](https://www.php.net/manual/es/language.types.php)