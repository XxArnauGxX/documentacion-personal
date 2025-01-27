# Clases en JavaScript

## Introducción

Las clases en JavaScript, introducidas en ES6, proporcionan una forma más clara y estructurada de trabajar con programación orientada a objetos (POO). Aunque internamente JavaScript sigue basándose en prototipos, las clases simplifican la creación de objetos y la herencia.

### Características principales
- Las clases son una plantilla para crear objetos.
- Proporcionan una sintaxis más intuitiva para definir métodos y propiedades.
- Facilitan la herencia y reutilización de código.

---

## Declaración de Clases

### Sintaxis básica

Se utiliza la palabra clave `class` para declarar una clase.

#### Ejemplo
```javascript
class Persona {
    constructor(nombre, edad) {
        this.nombre = nombre;
        this.edad = edad;
    }

    saludar() {
        return `Hola, me llamo ${this.nombre} y tengo ${this.edad} años.`;
    }
}

const juan = new Persona('Juan', 30);
console.log(juan.saludar()); // Hola, me llamo Juan y tengo 30 años.
```

---

## Constructores y Métodos

### Constructor
El método `constructor` es un método especial que se ejecuta automáticamente al crear una nueva instancia de una clase.

#### Ejemplo
```javascript
class Animal {
    constructor(tipo) {
        this.tipo = tipo;
    }
}

const perro = new Animal('mamífero');
console.log(perro.tipo); // mamífero
```

### Métodos
Son funciones definidas dentro de una clase que operan sobre las propiedades del objeto.

#### Ejemplo
```javascript
class Vehiculo {
    arrancar() {
        return 'El vehículo está arrancando.';
    }
}

const coche = new Vehiculo();
console.log(coche.arrancar()); // El vehículo está arrancando.
```

---

## Herencia

La herencia permite que una clase (hija) extienda otra clase (padre), heredando sus propiedades y métodos.

### Uso de `extends` y `super`

#### Ejemplo
```javascript
class Persona {
    constructor(nombre) {
        this.nombre = nombre;
    }

    saludar() {
        return `Hola, soy ${this.nombre}.`;
    }
}

class Estudiante extends Persona {
    constructor(nombre, curso) {
        super(nombre); // Llama al constructor de la clase padre
        this.curso = curso;
    }

    estudiar() {
        return `${this.nombre} está estudiando ${this.curso}.`;
    }
}

const ana = new Estudiante('Ana', 'JavaScript');
console.log(ana.saludar()); // Hola, soy Ana.
console.log(ana.estudiar()); // Ana está estudiando JavaScript.
```

---

## Propiedades Públicas y Privadas

### Propiedades Públicas
Se acceden directamente desde fuera de la clase.

#### Ejemplo
```javascript
class Producto {
    constructor(nombre, precio) {
        this.nombre = nombre;
        this.precio = precio;
    }
}

const libro = new Producto('Libro', 15);
console.log(libro.nombre); // Libro
```

### Propiedades Privadas
Se definen con el prefijo `#` y no pueden ser accedidas directamente desde fuera de la clase.

#### Ejemplo
```javascript
class CuentaBancaria {
    #saldo = 0;

    depositar(cantidad) {
        this.#saldo += cantidad;
    }

    verSaldo() {
        return `El saldo es ${this.#saldo} euros.`;
    }
}

const cuenta = new CuentaBancaria();
cuenta.depositar(100);
console.log(cuenta.verSaldo()); // El saldo es 100 euros.
```

---

## Métodos Estáticos

Los métodos estáticos son funciones que pertenecen a la clase y no a las instancias.

#### Ejemplo
```javascript
class Utilidad {
    static convertirEurosADolares(euros) {
        return euros * 1.1;
    }
}

console.log(Utilidad.convertirEurosADolares(100)); // 110
```

---

## Buenas Prácticas

- Usa nombres significativos para clases, métodos y propiedades.
- Divide responsabilidades: cada clase debe tener un propósito claro.
- Usa propiedades privadas para proteger datos sensibles.
- Documenta las clases y métodos para facilitar el mantenimiento del código.
- Prefiere la composición sobre la herencia si es posible para evitar acoplamientos innecesarios.