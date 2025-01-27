# Manipulación del DOM en JavaScript

## Introducción

El DOM (Document Object Model) es una representación estructurada de un documento HTML. En JavaScript, permite interactuar y manipular los elementos de una página web, como cambiar el contenido, modificar estilos o agregar nuevos elementos dinámicamente.

---

## Selección de Elementos

### Métodos más comunes

#### `getElementById`
Selecciona un elemento por su atributo `id`.
```javascript
const elemento = document.getElementById('miElemento');
console.log(elemento);
```

#### `querySelector` y `querySelectorAll`
Selecciona el primer elemento que coincida con un selector CSS o todos los elementos que coincidan, respectivamente.
```javascript
const primerElemento = document.querySelector('.miClase');
const todosLosElementos = document.querySelectorAll('.miClase');
```

#### `getElementsByClassName` y `getElementsByTagName`
Selecciona elementos por clase o por etiqueta.
```javascript
const elementosClase = document.getElementsByClassName('miClase');
const elementosEtiqueta = document.getElementsByTagName('div');
```

---

## Modificación del Contenido

### Propiedades principales

#### `innerHTML`
Permite cambiar el contenido HTML interno del elemento.
```javascript
document.getElementById('miElemento').innerHTML = '<p>Nuevo contenido</p>';
```

#### `textContent`
Modifica solo el texto interno, ignorando cualquier etiqueta HTML.
```javascript
document.getElementById('miElemento').textContent = 'Texto actualizado';
```

---

## Estilos y Clases

### Modificar estilos en línea

#### Usando la propiedad `style`
```javascript
const elemento = document.getElementById('miElemento');
elemento.style.color = 'red';
elemento.style.backgroundColor = 'yellow';
```

### Gestionar clases

#### Usando `classList`
- **`add`**: Agrega una clase.
- **`remove`**: Elimina una clase.
- **`toggle`**: Alterna una clase.
- **`contains`**: Verifica si un elemento tiene una clase.

```javascript
const elemento = document.getElementById('miElemento');
elemento.classList.add('nuevaClase');
elemento.classList.remove('antiguaClase');
if (elemento.classList.contains('nuevaClase')) {
    console.log('Tiene la clase nuevaClase');
}
elemento.classList.toggle('otraClase');
```

---

## Creación y Eliminación de Elementos

### Crear un nuevo elemento

#### Usando `createElement`
```javascript
const nuevoElemento = document.createElement('div');
nuevoElemento.textContent = 'Soy un nuevo div';
document.body.appendChild(nuevoElemento);
```

### Eliminar un elemento

#### Usando `remove`
```javascript
const elemento = document.getElementById('miElemento');
elemento.remove();
```

#### Usando `removeChild`
```javascript
const contenedor = document.getElementById('contenedor');
const hijo = document.getElementById('hijo');
contenedor.removeChild(hijo);
```

---

## Propiedades y Atributos

### Modificar atributos

#### `setAttribute` y `getAttribute`
```javascript
const enlace = document.querySelector('a');
enlace.setAttribute('href', 'https://www.ejemplo.com');
console.log(enlace.getAttribute('href'));
```

### Eliminar atributos

#### `removeAttribute`
```javascript
enlace.removeAttribute('target');
```

---

## Ejemplo Completo

```javascript
// Crear un nuevo párrafo
const parrafo = document.createElement('p');
parrafo.textContent = 'Este es un nuevo párrafo';

// Agregar una clase y estilos
parrafo.classList.add('miClase');
parrafo.style.color = 'blue';

// Agregar el párrafo al cuerpo del documento
const contenedor = document.getElementById('contenedor');
contenedor.appendChild(parrafo);

// Cambiar el contenido de un título existente
const titulo = document.getElementById('titulo');
titulo.textContent = 'Título actualizado';

// Eliminar un elemento
const eliminarElemento = document.getElementById('eliminar');
eliminarElemento.remove();
```

---

## Buenas Prácticas

- Selecciona elementos de forma eficiente usando `querySelector` o `querySelectorAll`.
- Evita usar `innerHTML` a menos que sea necesario, para prevenir vulnerabilidades de seguridad.
- Usa `classList` para manipular clases en lugar de sobrescribir la propiedad `className`.
- Prefiere la separación de estilos en CSS en lugar de aplicar estilos en línea.