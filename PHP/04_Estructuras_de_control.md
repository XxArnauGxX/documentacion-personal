# 04. Estructuras de Control en PHP

---

## 1. ¿Qué es una estructura de control?

Las **estructuras de control** permiten modificar el flujo de ejecución de un programa, decidiendo qué bloques de código se ejecutan o cuántas veces se repite una acción.

---

## 2. Estructura if/else

Permite ejecutar un bloque de código si se cumple una condición y otro si no se cumple.

```php
if (condición) {
    // Código si la condición es verdadera
} else {
    // Código si la condición es falsa
}
```

**Ejemplo:**

```php
$edad = 18;
if ($edad >= 18) {
    echo "Eres mayor de edad";
} else {
    echo "Eres menor de edad";
}
```

---

## 3. Estructura elseif

Permite evaluar varias condiciones diferentes en orden.

```php
if (condición1) {
    // Bloque 1
} elseif (condición2) {
    // Bloque 2
} else {
    // Bloque por defecto
}
```

**Ejemplo:**

```php
$nota = 7;
if ($nota >= 9) {
    echo "Sobresaliente";
} elseif ($nota >= 7) {
    echo "Notable";
} elseif ($nota >= 5) {
    echo "Aprobado";
} else {
    echo "Suspendido";
}
```

---

## 4. Estructura switch

Ideal para comparar una variable contra varios posibles valores.

```php
switch (variable) {
    case valor1:
        // Código si variable == valor1
        break;
    case valor2:
        // Código si variable == valor2
        break;
    default:
        // Código si ningún caso se cumple
}
```

**Ejemplo:**

```php
$dia = "lunes";
switch ($dia) {
    case "lunes":
        echo "Empieza la semana";
        break;
    case "viernes":
        echo "¡Por fin es viernes!";
        break;
    default:
        echo "Es un día normal";
}
```

---

## 5. Estructura match (PHP 8+)

La expresión `match` es una alternativa más moderna y estricta al `switch`. Compara una variable con varios valores posibles y devuelve directamente el resultado. Es más segura porque compara tipo y valor, y no necesita break.

```php
$resultado = match($valor) {
    1 => 'Uno',
    2 => 'Dos',
    3, 4 => 'Tres o cuatro',
    default => 'Otro valor',
};
echo $resultado;
```

**Ejemplo:**

```php
$dia = "lunes";
$mensaje = match($dia) {
    "lunes" => "Empieza la semana",
    "viernes" => "¡Por fin es viernes!",
    default => "Es un día normal",
};
echo $mensaje;
```

**Ventajas:**

* Compara tipo y valor (más seguro que switch)
* Permite devolver directamente el resultado
* Sintaxis más limpia y sin necesidad de break

---

## 6. Estructuras de repetición

Sirven para repetir un bloque de código varias veces.

### 6.1 while

Ejecuta el bloque **mientras** se cumpla la condición.

```php
$i = 1;
while ($i <= 5) {
    echo $i;
    $i++;
}
```

### 6.2 do-while

Primero ejecuta el bloque y **luego** verifica la condición (siempre ejecuta al menos una vez).

```php
$i = 1;
do {
    echo $i;
    $i++;
} while ($i <= 5);
```

### 6.3 for

Ideal para repetir cuando sabes cuántas veces quieres iterar.

```php
for ($i = 1; $i <= 5; $i++) {
    echo $i;
}
```

### 6.4 foreach

Sirve para recorrer arrays de manera sencilla.

```php
$colores = ["rojo", "verde", "azul"];
foreach ($colores as $color) {
    echo $color;
}
```

---

## 7. Control de flujo: break y continue

* **break:** Sale de la estructura de control (como un bucle o switch).
* **continue:** Salta a la siguiente iteración del bucle.

**Ejemplo con break:**

```php
for ($i = 1; $i <= 10; $i++) {
    if ($i == 5) {
        break; // Sale del bucle
    }
    echo $i;
}
```

**Ejemplo con continue:**

```php
for ($i = 1; $i <= 5; $i++) {
    if ($i == 3) {
        continue; // Salta el 3
    }
    echo $i;
}
```

---

## 8. Ejemplos prácticos

1. **Clasificación de edad:**

```php
$edad = 16;
if ($edad < 13) {
    echo "Niño/a";
} elseif ($edad < 18) {
    echo "Adolescente";
} else {
    echo "Adulto";
}
```

2. **Suma de los primeros 10 números:**

```php
$suma = 0;
for ($i = 1; $i <= 10; $i++) {
    $suma += $i;
}
echo $suma; // 55
```

3. **Mostrar todos los elementos de un array:**

```php
$frutas = ["manzana", "pera", "plátano"];
foreach ($frutas as $fruta) {
    echo $fruta;
}
```

4. **Ejemplo con match:**

```php
$nota = 8;
$calificacion = match(true) {
    $nota >= 9 => "Sobresaliente",
    $nota >= 7 => "Notable",
    $nota >= 5 => "Aprobado",
    default => "Suspendido",
};
echo $calificacion;
```

---

## 9. Errores comunes

* Olvidar las llaves `{}` en bloques con varias líneas.
* Condiciones mal planteadas (`=` en vez de `==`).
* Bucles infinitos por no actualizar la condición.
* Olvidar el break en switch (puede ejecutar varios casos seguidos).
* Usar match en PHP anteriores a la versión 8.

---

## 10. Recursos para practicar

* [W3Schools: PHP Control Structures](https://www.w3schools.com/php/php_if_else.asp)
* [Manual PHP - Control Structures](https://www.php.net/manual/es/language.control-structures.php)