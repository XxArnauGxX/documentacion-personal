# Eventos en JavaScript

## Introducción

Un evento en JavaScript es cualquier interacción que ocurra en una página web, como un clic del usuario, mover el ratón, presionar una tecla, entre otros. Los eventos son fundamentales para hacer que las páginas sean dinámicas e interactivas y mejorar la experiencia del usuario.

---

## Escucha de Eventos

### Usando `addEventListener`
El método `addEventListener` se utiliza para registrar un evento en un elemento.

#### Sintaxis
```javascript
elemento.addEventListener(tipoEvento, manejador);
```
- **`tipoEvento`**: Especifica el tipo de evento, como `'click'`, `'mouseover'`, `'keydown'`.
- **`manejador`**: Es una función que se ejecuta cuando ocurre el evento.

#### Ejemplo
```javascript
const boton = document.getElementById('miBoton');

boton.addEventListener('click', () => {
    alert('¡Botón clicado!');
});
```

---

## Tipos Comunes de Eventos

### Eventos de ratón
- **`click`**: Ocurre cuando se hace clic en un elemento.
- **`dblclick`**: Ocurre al hacer doble clic.
- **`mouseover`**: Cuando el ratón pasa sobre un elemento.
- **`mouseout`**: Cuando el ratón sale de un elemento.

#### Ejemplo
```javascript
const caja = document.getElementById('miCaja');

caja.addEventListener('mouseover', () => {
    caja.style.backgroundColor = 'yellow';
});

caja.addEventListener('mouseout', () => {
    caja.style.backgroundColor = 'white';
});
```

### Eventos de teclado
- **`keydown`**: Ocurre cuando se presiona una tecla.
- **`keyup`**: Ocurre cuando se suelta una tecla.
- **`keypress`**: Ocurre cuando se mantiene presionada una tecla (obsoleto en algunos navegadores).

#### Ejemplo
```javascript
document.addEventListener('keydown', (evento) => {
    console.log(`Tecla presionada: ${evento.key}`);
});
```

### Eventos de formulario
- **`submit`**: Ocurre cuando se envía un formulario.
- **`change`**: Ocurre cuando cambia el valor de un campo de formulario.
- **`input`**: Ocurre mientras se escribe en un campo de entrada.

#### Ejemplo
```javascript
const formulario = document.getElementById('miFormulario');

formulario.addEventListener('submit', (evento) => {
    evento.preventDefault(); // Evita el envío del formulario
    alert('Formulario enviado.');
});
```

---

## Delegación de Eventos

La delegación de eventos consiste en asignar un evento a un elemento padre en lugar de a cada hijo individual. Es útil cuando hay muchos elementos dinámicos o cuando se añaden elementos al DOM de manera dinámica.

#### Ejemplo
```javascript
const lista = document.getElementById('miLista');

lista.addEventListener('click', (evento) => {
    if (evento.target.tagName === 'LI') {
        console.log(`Elemento clicado: ${evento.target.textContent}`);
    }
});
```

---

## Remover Eventos

### Usando `removeEventListener`
Permite eliminar un evento previamente registrado. Es necesario que la función manejadora sea nombrada para poder referenciarla al eliminar el evento.

#### Ejemplo
```javascript
function mostrarMensaje() {
    alert('Evento activado.');
}

const boton = document.getElementById('miBoton');

boton.addEventListener('click', mostrarMensaje);
boton.removeEventListener('click', mostrarMensaje);
```

---

## Buenas Prácticas

- Usa `addEventListener` en lugar de asignar eventos directamente al atributo `onclick` o similar.
- Implementa la delegación de eventos para manejar elementos dinámicos o listas largas.
- Elimina eventos con `removeEventListener` cuando ya no sean necesarios, especialmente en elementos que se eliminan del DOM.
- Usa nombres descriptivos para las funciones manejadoras de eventos.
- Evita asignar múltiples escuchadores innecesarios al mismo elemento.