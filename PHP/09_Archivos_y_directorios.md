# 09. Archivos y Directorios en PHP

---

## 1. Introducción: ¿Para qué sirve manejar archivos?

Trabajar con archivos permite guardar información de manera permanente (por ejemplo, logs, datos de usuarios, registros, etc.), leer archivos de configuración o procesar documentos subidos por el usuario.

---

## 2. Abrir, leer y escribir archivos (fopen, fread, fwrite, fclose)

```php
$archivo = fopen('datos.txt', 'w'); // Abrir para escribir (w), crea el archivo si no existe
fwrite($archivo, "Hola, mundo!\n"); // Escribir en el archivo
fclose($archivo); // Cerrar archivo
```

Para leer:

```php
$archivo = fopen('datos.txt', 'r'); // Abrir solo lectura
$contenido = fread($archivo, filesize('datos.txt'));
echo $contenido;
fclose($archivo);
```

---

## 3. Leer y escribir archivos completos

* **Leer todo el archivo como string:**

```php
$texto = file_get_contents('datos.txt');
echo $texto;
```

* **Leer archivo como array de líneas:**

```php
$lineas = file('datos.txt');
foreach ($lineas as $linea) {
    echo $linea;
}
```

* **Escribir todo el archivo de una vez:**

```php
file_put_contents('nuevo.txt', "Texto a guardar\n");
```

---

## 4. Comprobar existencia y eliminar archivos

* **Comprobar si existe:**

```php
if (file_exists('datos.txt')) {
    echo "El archivo existe";
}
```

* **Eliminar archivo:**

```php
unlink('datos.txt');
```

---

## 5. Manejar directorios

* **Listar archivos y carpetas:**

```php
$archivos = scandir('.');
foreach ($archivos as $item) {
    echo $item . '<br>';
}
```

* **Crear y eliminar directorios:**

```php
mkdir('mi_carpeta');
rmdir('mi_carpeta');
```

* **Abrir y recorrer directorio manualmente:**

```php
$dir = opendir('.');
while (($item = readdir($dir)) !== false) {
    echo $item . '<br>';
}
closedir($dir);
```

---

## 6. Modificar permisos y propiedades

* **Cambiar nombre:**

```php
rename('archivo1.txt', 'archivo2.txt');
```

* **Copiar archivo:**

```php
copy('original.txt', 'copia.txt');
```

* **Ver tamaño:**

```php
echo filesize('copia.txt');
```

* **Cambiar permisos:**

```php
chmod('archivo.txt', 0644);
```

---

## 7. Manejo de errores al trabajar con archivos

Siempre comprueba si las operaciones han tenido éxito y controla posibles errores:

```php
$archivo = fopen('datos.txt', 'r');
if ($archivo === false) {
    echo "Error al abrir el archivo";
} else {
    // Operaciones normales
    fclose($archivo);
}
```

También puedes usar `@` para suprimir errores, pero es mejor capturarlos y gestionarlos correctamente.

---

## 8. Ejemplos prácticos

1. **Leer todas las líneas de un archivo y numerarlas:**

```php
$lineas = file('datos.txt');
foreach ($lineas as $num => $linea) {
    echo ($num+1) . ": " . $linea;
}
```

2. **Guardar un array en un archivo (uno por línea):**

```php
$frutas = ["manzana", "pera", "plátano"];
file_put_contents('frutas.txt', implode("\n", $frutas));
```

---

## 9. Errores comunes

* Olvidar cerrar el archivo (`fclose`).
* No comprobar si el archivo existe antes de abrirlo.
* Permisos insuficientes para leer/escribir.
* Olvidar el modo correcto al abrir (w/r/a).
* Acceder a directorios/carpetas protegidos.

---

## 10. Recursos para practicar

* [W3Schools: PHP File Handling](https://www.w3schools.com/php/php_file.asp)
* [Manual PHP - Filesystem Functions](https://www.php.net/manual/es/book.filesystem.php)