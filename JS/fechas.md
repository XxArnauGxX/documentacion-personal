# Fechas y Tiempos en JavaScript

## 1. Introducción

JavaScript proporciona el objeto **`Date`** para trabajar con fechas y tiempos. Permite crear, manipular y formatear fechas de manera eficiente.

```js
let fechaActual = new Date();
console.log(fechaActual); // Muestra la fecha y hora actual
```

---

## 2. Creación de Fechas en JavaScript

### 2.1 Crear un Objeto `Date` con la Fecha y Hora Actual
```js
let ahora = new Date();
console.log(ahora);
```

### 2.2 Crear una Fecha con una Fecha Específica
```js
let fechaEspecifica = new Date(2024, 5, 15); // Año, Mes (0-based), Día
console.log(fechaEspecifica);
```

### 2.3 Crear una Fecha con Año, Mes, Día, Hora, Minuto y Segundo
```js
let fechaCompleta = new Date(2024, 5, 15, 14, 30, 0);
console.log(fechaCompleta);
```

### 2.4 Crear una Fecha a partir de una Cadena
```js
let fechaTexto = new Date("2024-06-15T14:30:00");
console.log(fechaTexto);
```

### 2.5 Crear una Fecha a partir de un Timestamp
```js
let fechaTimestamp = new Date(1718452200000);
console.log(fechaTimestamp);
```

---

## 3. Obtener Componentes de una Fecha

### 3.1 Obtener Año, Mes, Día, Hora, Minuto y Segundo
```js
let fecha = new Date();
console.log(fecha.getFullYear()); // Año
console.log(fecha.getMonth()); // Mes (0 = Enero, 11 = Diciembre)
console.log(fecha.getDate()); // Día del mes
console.log(fecha.getDay()); // Día de la semana (0 = Domingo, 6 = Sábado)
console.log(fecha.getHours()); // Hora
console.log(fecha.getMinutes()); // Minutos
console.log(fecha.getSeconds()); // Segundos
```

---

## 4. Modificar Fechas

### 4.1 Cambiar Año, Mes, Día, Hora, Minuto y Segundo
```js
let fechaModificada = new Date();
fechaModificada.setFullYear(2025);
fechaModificada.setMonth(11); // Diciembre
fechaModificada.setDate(25);
fechaModificada.setHours(12);
fechaModificada.setMinutes(45);
console.log(fechaModificada);
```

---

## 5. Operaciones con Fechas

### 5.1 Comparar Fechas
```js
let fecha1 = new Date("2024-06-15");
let fecha2 = new Date("2023-12-25");

console.log(fecha1 > fecha2); // true
console.log(fecha1 < fecha2); // false
```

### 5.2 Diferencia entre Fechas (Milisegundos a Días)
```js
let inicio = new Date("2024-01-01");
let fin = new Date("2024-12-31");
let diferencia = fin - inicio;
let diasDiferencia = diferencia / (1000 * 60 * 60 * 24);
console.log(diasDiferencia); // 364 días
```

### 5.3 Formatear Fechas en Cadena
```js
let fechaFormateada = new Date();
console.log(fechaFormateada.toDateString()); // "Mon Jun 15 2024"
console.log(fechaFormateada.toISOString()); // "2024-06-15T12:00:00.000Z"
console.log(fechaFormateada.toLocaleDateString("es-ES")); // "15/6/2024"
```

---

## 6. Uso de `Intl.DateTimeFormat` para Formateo Avanzado

```js
let fechaEjemplo = new Date();
let opciones = { weekday: "long", year: "numeric", month: "long", day: "numeric" };
console.log(new Intl.DateTimeFormat("es-ES", opciones).format(fechaEjemplo)); // "sábado, 15 de junio de 2024"
```

---

## 7. Librerías Populares para Manejo de Fechas

### 7.1 Day.js (Ligera y Rápida)
```js
import dayjs from "dayjs";
console.log(dayjs().format("YYYY-MM-DD"));
```

### 7.2 Date-fns (Múltiples Funciones Útiles)
```js
import { format, addDays } from "date-fns";
console.log(format(new Date(), "dd/MM/yyyy"));
```

### 7.3 Moment.js (Antiguo pero Completo)
```js
import moment from "moment";
console.log(moment().format("DD/MM/YYYY"));
```