# Módulos en JavaScript

## Introducción

Los módulos en JavaScript permiten dividir el código en pequeños archivos reutilizables. Introducidos en ES6, los módulos mejoran la organización del código, facilitan su mantenimiento y fomentan la reutilización en proyectos grandes o colaborativos.

---

## Conceptos Básicos

1. **Exportar**: Un módulo puede exponer funciones, objetos o variables para que otros archivos puedan utilizarlos.
2. **Importar**: Otro módulo puede usar lo que ha sido exportado desde otro archivo.

---

## Exportar Contenido

### Exportación Nombrada
Permite exportar múltiples elementos desde un módulo.

#### Sintaxis
```javascript
// archivo: utilidades.js
export const sumar = (a, b) => a + b;
export const restar = (a, b) => a - b;
```

#### Importar una exportación nombrada
```javascript
// archivo: app.js
import { sumar, restar } from './utilidades.js';

console.log(sumar(5, 3)); // 8
console.log(restar(5, 3)); // 2
```

### Exportación por Defecto
Cada módulo puede tener una única exportación por defecto, generalmente utilizada para exportar el contenido principal del archivo.

#### Sintaxis
```javascript
// archivo: calculadora.js
export default function multiplicar(a, b) {
    return a * b;
}
```

#### Importar una exportación por defecto
```javascript
// archivo: app.js
import multiplicar from './calculadora.js';

console.log(multiplicar(4, 2)); // 8
```

### Exportación Combinada
Se pueden combinar exportaciones nombradas y por defecto en un solo archivo.

#### Ejemplo
```javascript
// archivo: herramientas.js
export const dividir = (a, b) => a / b;
export default function potencia(a, b) {
    return a ** b;
}
```

#### Importación
```javascript
// archivo: app.js
import potencia, { dividir } from './herramientas.js';

console.log(potencia(2, 3)); // 8
console.log(dividir(10, 2)); // 5
```

---

## Alias para Importación y Exportación

### Renombrar exportaciones
```javascript
// archivo: operaciones.js
export const suma = (a, b) => a + b;
export const resta = (a, b) => a - b;
```

### Renombrar al importar
```javascript
// archivo: app.js
import { suma as agregar, resta como sustraer } from './operaciones.js';

console.log(agregar(10, 5)); // 15
console.log(sustraer(10, 5)); // 5
```

---

## Importar Todo

Puedes importar todo el contenido exportado de un módulo como un objeto.

#### Ejemplo
```javascript
// archivo: matematicas.js
export const suma = (a, b) => a + b;
export const resta = (a, b) => a - b;
export const multiplicacion = (a, b) => a * b;
```

```javascript
// archivo: app.js
import * as matematicas from './matematicas.js';

console.log(matematicas.suma(4, 3)); // 7
console.log(matematicas.resta(10, 2)); // 8
console.log(matematicas.multiplicacion(3, 5)); // 15
```

---

## Uso de Módulos en el Navegador

Para usar módulos directamente en el navegador, necesitas:

1. Asegurarte de que el archivo tenga la extensión `.js`.
2. Declarar el atributo `type="module"` en el `<script>`.

#### Ejemplo
```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Módulos en el Navegador</title>
</head>
<body>
    <script type="module">
        import { sumar } from './utilidades.js';
        console.log(sumar(2, 3));
    </script>
</body>
</html>
```

---

## Buenas Prácticas

1. **Usa exportaciones por defecto para contenido principal:** Facilita la importación en otros archivos.
2. **Agrupa funciones relacionadas en módulos:** Mantén tu código modular y organizado.
3. **Usa nombres descriptivos para funciones y módulos:** Mejora la legibilidad y mantenibilidad.
4. **Evita importar todo a menos que sea necesario:** Ayuda a reducir el tamaño del archivo y mejora el rendimiento.