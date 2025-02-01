# 📌 Transiciones, Animaciones y Transformaciones en CSS

CSS permite agregar dinamismo y fluidez a los elementos de una página web mediante **transiciones**, **animaciones** y **transformaciones**. Estos efectos mejoran la experiencia del usuario sin necesidad de JavaScript.

---

## 🎯 **Transiciones en CSS**
Las transiciones permiten cambiar valores de propiedades CSS de forma animada, generando efectos más suaves y atractivos.

### 🔹 **Propiedad `transition`**
```css
.elemento {
    transition: propiedad duración función-retardo;
}
```
Ejemplo básico:
```css
.boton {
    background-color: blue;
    transition: background-color 0.5s ease-in-out;
}
.boton:hover {
    background-color: red;
}
```
📌 **Efecto:** Cuando el usuario pasa el cursor sobre el botón, el color cambia suavemente en `0.5s`.

### 🔹 **Propiedades de `transition`**
| Propiedad | Descripción |
|-----------|------------|
| `transition-property` | Propiedad a animar (ej. `opacity`, `width`). |
| `transition-duration` | Duración de la transición (ej. `0.5s`). |
| `transition-timing-function` | Controla la aceleración/desaceleración. |
| `transition-delay` | Retraso antes de iniciar la transición. |

### 🔹 **Valores de `transition-timing-function`**
| Valor | Descripción |
|--------|-------------|
| `linear` | Velocidad constante. |
| `ease` | Comienza lento, acelera y termina lento. |
| `ease-in` | Comienza lento y acelera. |
| `ease-out` | Comienza rápido y desacelera. |
| `ease-in-out` | Comienza y termina lento. |

Ejemplo con varios efectos:
```css
.caja {
    width: 100px;
    height: 100px;
    background-color: green;
    transition: all 0.5s ease-in-out;
}
.caja:hover {
    width: 200px;
    height: 200px;
    background-color: yellow;
}
```
📌 **Efecto:** La caja crece de tamaño y cambia de color al pasar el cursor.

---

## 🎞️ **Animaciones en CSS**
Las animaciones permiten crear efectos más complejos y repetitivos mediante `@keyframes`.

### 🔹 **Estructura de una animación**
```css
@keyframes nombreAnimacion {
    from { propiedad: valor-inicial; }
    to { propiedad: valor-final; }
}
```
Ejemplo básico:
```css
@keyframes mover {
    from {
        transform: translateX(0px);
    }
    to {
        transform: translateX(200px);
    }
}
.caja {
    animation: mover 2s ease-in-out infinite alternate;
}
```
📌 **Efecto:** La caja se mueve de lado a lado continuamente.

### 🔹 **Propiedades de `animation`**
| Propiedad | Descripción |
|-----------|------------|
| `animation-name` | Nombre de la animación. |
| `animation-duration` | Duración de la animación. |
| `animation-timing-function` | Control de aceleración/desaceleración. |
| `animation-delay` | Retraso antes de iniciar la animación. |
| `animation-iteration-count` | Número de repeticiones (`infinite` para infinitas). |
| `animation-direction` | Dirección (`normal`, `reverse`, `alternate`). |

Ejemplo con `animation-direction`:
```css
@keyframes rotar {
    0% { transform: rotate(0deg); }
    100% { transform: rotate(360deg); }
}
.circulo {
    animation: rotar 3s linear infinite;
}
```
📌 **Efecto:** El elemento gira continuamente.

---

## 🌀 **Transformaciones en CSS**
Las transformaciones permiten modificar la forma, el tamaño y la posición de los elementos sin afectar su flujo en la página.

### 🔹 **Propiedad `transform`**
```css
.elemento {
    transform: función(valor);
}
```

### 🔹 **Funciones de Transformación**
| Función | Descripción |
|---------|------------|
| `translate(x, y)` | Desplaza el elemento en el eje X e Y. |
| `rotate(deg)` | Rota el elemento. |
| `scale(x, y)` | Escala el tamaño del elemento. |
| `skew(x, y)` | Inclina el elemento. |
| `matrix(n, n, n, n, n, n)` | Combinación de transformaciones. |

### 🎯 **Ejemplo de Uso**
```css
.caja {
    transform: translate(50px, 20px) rotate(45deg) scale(1.2);
}
```
📌 **Efecto:** La caja se desplaza, rota e incrementa su tamaño.

### 🔹 **Transformaciones en 3D**
| Función | Descripción |
|---------|------------|
| `rotateX(deg)` | Rota en el eje X. |
| `rotateY(deg)` | Rota en el eje Y. |
| `perspective(px)` | Agrega profundidad 3D. |

Ejemplo de rotación en 3D:
```css
.cubo {
    transform: rotateY(180deg);
}
```
📌 **Efecto:** El elemento gira en el eje Y.

---

## 🏆 **Conclusión**
- Usa **transiciones** para cambios suaves de propiedades CSS.
- Usa **animaciones** con `@keyframes` para efectos repetitivos y avanzados.
- Usa **transformaciones** para modificar la apariencia y posición de los elementos.
- Combina estos efectos para interfaces más dinámicas y atractivas.

🚀 **¡Implementa estos efectos en tus proyectos y haz que tu diseño cobre vida!**