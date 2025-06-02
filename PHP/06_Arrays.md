# 06. Arrays en PHP

---

## 1. ¿Qué es un array?

Un **array** es una variable especial que puede almacenar varios valores (elementos) en una sola estructura, en vez de tener que crear una variable para cada valor.

---

## 2. Tipos de arrays

* **Array indexado:** Los elementos se identifican por un índice numérico (empieza en 0).
* **Array asociativo:** Los elementos se identifican por una clave (string) personalizada.
* **Array multidimensional:** Un array que contiene otros arrays dentro.

---

## 3. Crear y acceder a elementos de un array

**Array indexado:**

```php
$frutas = ["manzana", "pera", "plátano"];
echo $frutas[0]; // manzana
echo $frutas[2]; // plátano
```

Se pueden crear también con `array()`:

```php
$numeros = array(1, 2, 3, 4);
```

Agregar elementos:

```php
$frutas[] = "naranja"; // Añade al final
```

---

## 4. Recorrer arrays

### Con for:

```php
for ($i = 0; $i < count($frutas); $i++) {
    echo $frutas[$i];
}
```

### Con foreach:

```php
foreach ($frutas as $fruta) {
    echo $fruta;
}
```

---

## 5. Arrays asociativos

Usan claves personalizadas (strings) en vez de índices numéricos.

```php
$persona = [
    "nombre" => "Arnau",
    "edad" => 20,
    "profesion" => "desarrollador"
];
echo $persona["nombre"];
```

Recorrer un array asociativo:

```php
foreach ($persona as $clave => $valor) {
    echo "$clave: $valor<br>";
}
```

---

## 6. Arrays multidimensionales

Son arrays que contienen otros arrays como elementos.

```php
$matriz = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
];
echo $matriz[1][2]; // 6
```

Ejemplo de array asociativo multidimensional:

```php
$alumnos = [
    ["nombre" => "Ana", "nota" => 8],
    ["nombre" => "Luis", "nota" => 6]
];
echo $alumnos[0]["nombre"]; // Ana
```

---

## 7. Funciones útiles para arrays

* `count($array)`: Devuelve el número de elementos.
* `array_push($array, $valor)`: Añade elementos al final.
* `array_pop($array)`: Elimina el último elemento.
* `array_shift($array)`: Elimina el primer elemento.
* `array_unshift($array, $valor)`: Añade elementos al principio.
* `in_array($valor, $array)`: Comprueba si un valor está en el array.
* `array_keys($array)`: Devuelve todas las claves del array.
* `array_values($array)`: Devuelve todos los valores del array.

---

## 8. Ejemplos prácticos

**Sumar todos los elementos de un array:**

```php
$numeros = [1, 2, 3, 4, 5];
$suma = 0;
foreach ($numeros as $num) {
    $suma += $num;
}
echo $suma; // 15
```

**Buscar en un array:**

```php
$colores = ["rojo", "azul", "verde"];
if (in_array("azul", $colores)) {
    echo "El color está en el array";
}
```

---

## 9. Errores comunes

* Confundir el índice o la clave de acceso.
* Intentar acceder a un índice que no existe (da error o warning).
* Olvidar que los arrays empiezan en índice 0.
* Mezclar tipos de claves en el mismo array (mejor evitarlo para arrays sencillos).

---

## 10. Recursos para practicar

* [W3Schools: PHP Arrays](https://www.w3schools.com/php/php_arrays.asp)
* [Manual PHP - Arrays](https://www.php.net/manual/es/language.types.array.php)