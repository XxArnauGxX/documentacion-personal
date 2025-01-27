# Objetos en JavaScript

## Introducción

Los objetos en JavaScript son colecciones de pares clave-valor, donde las claves son cadenas (o `Symbol`) y los valores pueden ser cualquier tipo de dato, incluyendo otros objetos o funciones. Los objetos son fundamentales en JavaScript, ya que casi todo en el lenguaje es un objeto o se basa en ellos.

### Características principales
- Son dinámicos, es decir, pueden modificarse en tiempo de ejecución.
- Las claves se convierten automáticamente en cadenas.
- Permiten almacenar datos estructurados y complejos.

---

## Creación de Objetos

### Objeto literal
La forma más común y sencilla de crear un objeto es usando llaves `{}`.

#### Ejemplo
```javascript
const persona = {
    nombre: 'Juan',
    edad: 30,
    esEstudiante: true
};
console.log(persona.nombre); // Juan
```

### Constructor `Object`
Otra forma es usando el constructor `Object`.

#### Ejemplo
```javascript
const persona = new Object();
persona.nombre = 'Ana';
persona.edad = 25;
console.log(persona); // { nombre: 'Ana', edad: 25 }
```

---

## Acceso y Modificación de Propiedades

### Notación de punto
Se utiliza para acceder a propiedades directamente por su nombre.

#### Ejemplo
```javascript
console.log(persona.nombre); // Ana
persona.edad = 26;
console.log(persona.edad); // 26
```

### Notación de corchetes
Permite acceder a propiedades usando cadenas dinámicas.

#### Ejemplo
```javascript
const clave = 'nombre';
console.log(persona[clave]); // Ana
persona['edad'] = 27;
console.log(persona['edad']); // 27
```

---

## Métodos de Objetos

### `Object.keys`
Devuelve un array con las claves del objeto.

#### Ejemplo
```javascript
console.log(Object.keys(persona)); // ['nombre', 'edad']
```

### `Object.values`
Devuelve un array con los valores del objeto.

#### Ejemplo
```javascript
console.log(Object.values(persona)); // ['Ana', 27]
```

### `Object.entries`
Devuelve un array de pares clave-valor.

#### Ejemplo
```javascript
console.log(Object.entries(persona)); // [['nombre', 'Ana'], ['edad', 27]]
```

---

## Iteración sobre Objetos

### Usando `for...in`
Itera sobre las claves de un objeto.

#### Ejemplo
```javascript
for (const clave in persona) {
    console.log(`${clave}: ${persona[clave]}`);
}
```

---

## Anidamiento de Objetos

Los objetos pueden contener otros objetos como valores, permitiendo estructuras complejas.

#### Ejemplo
```javascript
const estudiante = {
    nombre: 'Carlos',
    curso: {
        nombre: 'JavaScript',
        duracion: '3 meses'
    }
};
console.log(estudiante.curso.nombre); // JavaScript
```

---

## Manipulación Avanzada

### Desestructuración
Extrae propiedades de un objeto en variables individuales.

#### Ejemplo
```javascript
const { nombre, edad } = persona;
console.log(nombre, edad); // Ana 27
```

### Operador de propagación (`...`)
Crea copias o combina objetos.

#### Ejemplo
```javascript
const datosAdicionales = { profesion: 'Ingeniera' };
const nuevaPersona = { ...persona, ...datosAdicionales };
console.log(nuevaPersona); // { nombre: 'Ana', edad: 27, profesion: 'Ingeniera' }
```

---

## Buenas Prácticas

- Usa nombres descriptivos para las claves del objeto.
- Evita mutar objetos originales; usa el operador de propagación para crear copias.
- Valida la existencia de propiedades antes de acceder a ellas.
- Usa métodos como `Object.freeze` para evitar modificaciones no deseadas en objetos.

#### Ejemplo
```javascript
Object.freeze(persona);
persona.edad = 35; // No tendrá efecto
console.log(persona.edad); // 27
```