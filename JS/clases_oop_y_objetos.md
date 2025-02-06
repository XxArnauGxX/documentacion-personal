# Clases, Programación Orientada a Objetos (OOP) y Objetos en JavaScript

## 1. Introducción a la Programación Orientada a Objetos (OOP)

JavaScript es un lenguaje **multiparadigma**, lo que significa que soporta tanto programación **imperativa**, **funcional** y **orientada a objetos (OOP)**. La OOP se basa en el uso de **clases** y **objetos** para modelar datos del mundo real.

### ¿Qué son los objetos en JavaScript?
Los objetos son colecciones de propiedades clave-valor que representan entidades.
```js
let persona = {
    nombre: "Juan",
    edad: 30,
    saludar: function() {
        console.log("Hola, soy " + this.nombre);
    }
};

persona.saludar(); // "Hola, soy Juan"
```

---

## 2. Creación y Manipulación de Objetos

### 2.1 Creación de un Objeto Literal
```js
let coche = {
    marca: "Toyota",
    modelo: "Corolla",
    anio: 2022
};
```

### 2.2 Acceder y Modificar Propiedades
```js
console.log(coche.marca); // "Toyota"
coche.color = "Rojo"; // Agregar nueva propiedad
coche.anio = 2023; // Modificar propiedad existente
```

### 2.3 Métodos en Objetos
```js
let usuario = {
    nombre: "Ana",
    edad: 25,
    saludar() {
        console.log(`Hola, soy ${this.nombre}`);
    }
};
usuario.saludar();
```

### 2.4 Recorrer un Objeto con `for...in`
```js
for (let propiedad in usuario) {
    console.log(`${propiedad}: ${usuario[propiedad]}`);
}
```

---

## 3. Prototipos en JavaScript

JavaScript usa **herencia prototípica**, lo que significa que los objetos pueden heredar propiedades y métodos de otros objetos mediante prototipos.

### 3.1 Creación de un Obtotipo
```js
function Animal(nombre) {
    this.nombre = nombre;
}

Animal.prototype.hablar = function() {
    console.log(`${this.nombre} hace un sonido`);
};

let perro = new Animal("Firulais");
perro.hablar(); // "Firulais hace un sonido"
```

### 3.2 Sobreescritura de Métodos Prototípicos
```js
Animal.prototype.hablar = function() {
    console.log(`${this.nombre} ladra`);
};
perro.hablar(); // "Firulais ladra"
```

---

## 4. Clases en JavaScript (ES6)

A partir de ES6, JavaScript introdujo la sintaxis de **clases**, facilitando la creación de objetos con una sintaxis más clara.

### 4.1 Definir una Clase
```js
class Persona {
    constructor(nombre, edad) {
        this.nombre = nombre;
        this.edad = edad;
    }

    saludar() {
        console.log(`Hola, soy ${this.nombre} y tengo ${this.edad} años.`);
    }
}

let persona1 = new Persona("Carlos", 28);
persona1.saludar();
```

### 4.2 Herencia en Clases
```js
class Estudiante extends Persona {
    constructor(nombre, edad, curso) {
        super(nombre, edad);
        this.curso = curso;
    }
    estudiar() {
        console.log(`${this.nombre} está estudiando ${this.curso}`);
    }
}

let estudiante1 = new Estudiante("Laura", 22, "Matemáticas");
estudiante1.saludar(); // Hereda el método de Persona
iestudiante1.estudiar();
```

### 4.3 Métodos `getters` y `setters`
```js
class Circulo {
    constructor(radio) {
        this._radio = radio;
    }
    get radio() {
        return this._radio;
    }
    set radio(nuevoRadio) {
        if (nuevoRadio > 0) {
            this._radio = nuevoRadio;
        } else {
            console.log("El radio debe ser mayor que 0");
        }
    }
}

let c = new Circulo(10);
console.log(c.radio);
c.radio = 15; // Modifica el radio
```

---

## 5. Objetos Avanzados

### 5.1 `Object.keys`, `Object.values`, `Object.entries`
```js
let libro = {
    titulo: "El Principito",
    autor: "Antoine de Saint-Exupéry",
    año: 1943
};

console.log(Object.keys(libro)); // ["titulo", "autor", "año"]
console.log(Object.values(libro)); // ["El Principito", "Antoine de Saint-Exupéry", 1943]
console.log(Object.entries(libro));
```

### 5.2 Clonación de Objetos
```js
let copiaLibro = Object.assign({}, libro);
```
Otra forma:
```js
let copiaLibro2 = { ...libro };
```

### 5.3 `Object.freeze` y `Object.seal`
```js
let configuracion = { modoOscuro: true };
Object.freeze(configuracion);
configuracion.modoOscuro = false; // No se modifica
```

```js
let usuario = { nombre: "Luis" };
Object.seal(usuario);
usuario.nombre = "Pedro"; // Se puede modificar
usuario.edad = 30; // No se puede agregar
```