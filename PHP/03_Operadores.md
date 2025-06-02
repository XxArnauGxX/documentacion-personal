# 03. Operadores en PHP

---

## 1. ¿Qué es un operador?

Un **operador** es un símbolo o palabra especial que sirve para realizar operaciones sobre variables y valores. Por ejemplo, sumar, restar, comparar, o combinar resultados.

---

## 2. Operadores aritméticos

Sirven para realizar operaciones matemáticas básicas:

| Operador | Descripción              | Ejemplo      |
| -------- | ------------------------ | ------------ |
| +        | Suma                     | \$a + \$b    |
| -        | Resta                    | \$a - \$b    |
| \*       | Multiplicación           | \$a \* \$b   |
| /        | División                 | \$a / \$b    |
| %        | Módulo (resto)           | \$a % \$b    |
| \*\*     | Potencia (desde PHP 5.6) | \$a \*\* \$b |

**Ejemplo:**

```php
$a = 10;
$b = 3;
echo $a + $b;    // 13
echo $a % $b;    // 1
```

---

## 3. Operadores de asignación

Sirven para asignar o actualizar valores en variables:

| Operador | Descripción         | Ejemplo                    |
| -------- | ------------------- | -------------------------- |
| =        | Asignación simple   | \$a = 5                    |
| +=       | Suma y asigna       | \$a += 2; // \$a = \$a + 2 |
| -=       | Resta y asigna      | \$a -= 2;                  |
| \*=      | Multiplica y asigna | \$a \*= 2;                 |
| /=       | Divide y asigna     | \$a /= 2;                  |
| %=       | Módulo y asigna     | \$a %= 2;                  |
| \*\*=    | Potencia y asigna   | \$a \*\*= 3;               |

---

## 4. Operadores de comparación

Comparan dos valores y devuelven un resultado booleano (`true` o `false`):

| Operador | Descripción              | Ejemplo     |
| -------- | ------------------------ | ----------- |
| ==       | Igual que                | \$a == \$b  |
| ===      | Igual en valor y tipo    | \$a === \$b |
| != o <>  | Distinto que             | \$a != \$b  |
| !==      | Distinto en valor o tipo | \$a !== \$b |
| <        | Menor que                | \$a < \$b   |
| >        | Mayor que                | \$a > \$b   |
| <=       | Menor o igual que        | \$a <= \$b  |
| >=       | Mayor o igual que        | \$a >= \$b  |

**Ejemplo:**

```php
$a = 5;
$b = "5";
var_dump($a == $b);    // true
var_dump($a === $b);   // false
```

---

## 5. Operadores lógicos

Permiten combinar condiciones lógicas:

| Operador | Nombre | Ejemplo         | Resultado                                 |
|----------|--------|-----------------|-------------------------------------------|
| &&       | AND    | \$a && \$b      | true si ambos son true                    |
| and      | AND    | \$a and \$b     | igual que &&                              |
| \|\|     | OR     | \$a \|\| \$b    | true si alguno es true                    |
| or       | OR     | \$a or \$b      | igual que \|\|                            |
| !        | NOT    | !\$a            | true si \$a es false                      |
| xor      | XOR    | \$a xor \$b     | true si solo uno de los dos es true       |

---

## 6. Operadores de incremento y decremento

Permiten sumar o restar 1 a una variable de forma rápida:

| Operador | Descripción     | Ejemplo                             |
| -------- | --------------- | ----------------------------------- |
| ++\$a    | Pre-incremento  | \$a = 5; ++\$a; // \$a es 6         |
| \$a++    | Post-incremento | \$a = 5; \$a++; // \$a es 6 después |
| --\$a    | Pre-decremento  | \$a = 5; --\$a; // \$a es 4         |
| \$a--    | Post-decremento | \$a = 5; \$a--; // \$a es 4 después |

---

## 7. Operadores de concatenación

Para unir cadenas de texto se usa el punto (`.`):

```php
$nombre = "Arnau";
apellido = "García";
$completo = $nombre . " " . $apellido;
echo $completo;  // Arnau García
```

---

## 8. Ejemplos prácticos

```php
<?php
$a = 8;
$b = 4;

// Operadores aritméticos
echo $a + $b; // 12
echo $a / $b; // 2

// Operadores de asignación
$a += 2;      // $a ahora vale 10

// Comparación
var_dump($a == 10); // true

// Lógicos
$c = true;
$d = false;
var_dump($c && $d); // false

// Concatenación
$saludo = "Hola, " . $nombre;
echo $saludo;
?>
```

---

## 9. Errores comunes

* Usar `=` (asignación) en vez de `==` (comparación).
* Confundir `==` con `===` (igualdad estricta).
* Olvidar el punto `.` en la concatenación de cadenas.
* Mezclar operadores lógicos (`and`, `&&`) sin entender precedencia.
* Usar post-incremento o pre-incremento sin entender cuándo se suma realmente.

---

## 10. Recursos para practicar

* [W3Schools: PHP Operators](https://www.w3schools.com/php/php_operators.asp)
* [Manual PHP - Operadores](https://www.php.net/manual/es/language.operators.php)