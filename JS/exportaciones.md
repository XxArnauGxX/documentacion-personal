# Módulos en JavaScript: Import y Export

## 1. Introducción a los Módulos en JavaScript

Los **módulos** en JavaScript permiten dividir el código en archivos separados para mejorar la organización y reutilización del código. A partir de **ES6**, JavaScript introdujo el sistema de **import/export** para manejar módulos de manera nativa.

Antes de ES6, los desarrolladores usaban librerías como **CommonJS** (en Node.js) y **AMD** (en el navegador) para manejar módulos.

---

## 2. Exportando Módulos

### 2.1 Exportación Nombrada (`export`)

Podemos exportar múltiples elementos desde un archivo utilizando `export`.

```js
// archivo funciones.js
export function sumar(a, b) {
    return a + b;
}

export function restar(a, b) {
    return a - b;
}
```

O bien, exportarlos en una sola línea:
```js
export { sumar, restar };
```

### 2.2 Exportación por Defecto (`export default`)

Cada módulo puede tener **una única exportación por defecto**.

```js
// archivo calculadora.js
export default function multiplicar(a, b) {
    return a * b;
}
```

---

## 3. Importando Módulos

### 3.1 Importación de una Exportación Nombrada
Para importar una función específica de un módulo:
```js
import { sumar, restar } from "./funciones.js";
console.log(sumar(5, 3)); // 8
```

También es posible importar y asignar un alias:
```js
import { sumar as add } from "./funciones.js";
console.log(add(5, 3)); // 8
```

### 3.2 Importación de una Exportación por Defecto
Cuando un módulo tiene `export default`, se importa sin llaves `{}`.
```js
import multiplicar from "./calculadora.js";
console.log(multiplicar(4, 2)); // 8
```

### 3.3 Importar Todo un Módulo
Podemos importar **todo un módulo** usando `* as nombre`:
```js
import * as calculadora from "./funciones.js";
console.log(calculadora.sumar(3, 2)); // 5
console.log(calculadora.restar(3, 2)); // 1
```

---

## 4. Uso de Módulos en HTML

Para utilizar módulos en el navegador, debemos especificar `type="module"` en el `<script>` de HTML.

```html
<script type="module" src="app.js"></script>
```

Las principales diferencias al usar módulos en HTML:
✅ `type="module"` evita la ejecución global.
✅ Las importaciones solo funcionan en servidores HTTP, no en archivos locales (`file://`).
✅ Se ejecutan en modo **strict** (`use strict` activado por defecto).

---

## 5. Dynamic Imports (`import()`) en JavaScript

Con `import()`, podemos **cargar módulos de manera dinámica**, lo que permite una carga diferida (`lazy loading`).

```js
if (usuarioAutenticado) {
    import("./dashboard.js").then(modulo => {
        modulo.mostrarDashboard();
    });
}
```

También podemos usar `await` dentro de una función `async`:
```js
async function cargarModulo() {
    const modulo = await import("./utilidades.js");
    modulo.funcionUtil();
}
cargarModulo();
```

---

## 6. Diferencias entre Import/Export y CommonJS

| Característica        | Import/Export (ESM) | CommonJS (Node.js) |
|----------------------|-------------------|------------------|
| Sintaxis            | `import/export`   | `require/module.exports` |
| Soporte en Navegador | ✅ Sí              | ❌ No            |
| Soporte en Node.js  | ✅ Desde ES6       | ✅ Sí (por defecto) |
| Carga de Módulos    | Asíncrona         | Síncrona         |

Ejemplo de **CommonJS** en Node.js:
```js
// archivo funciones.js
module.exports = {
    sumar: (a, b) => a + b,
    restar: (a, b) => a - b
};
```
```js
// archivo app.js
const funciones = require("./funciones.js");
console.log(funciones.sumar(2, 3)); // 5
```