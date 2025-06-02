# 08. Programación Orientada a Objetos (POO) en PHP

---

## 1. ¿Qué es la programación orientada a objetos?

La **POO** es un paradigma de programación basado en "objetos" que agrupan datos y funcionalidades. Permite modelar el mundo real, favorece la reutilización y el mantenimiento del código.

---

## 2. Clases y objetos

* **Clase:** Plantilla o molde para crear objetos.
* **Objeto:** Instancia concreta de una clase.

```php
class Coche {
    // Definición de la clase
}
$miCoche = new Coche();
```

---

## 3. Propiedades y métodos

* **Propiedad:** Variable de una clase/objeto.
* **Método:** Función de una clase/objeto.

```php
class Persona {
    public $nombre;
    public function saludar() {
        echo "Hola, soy $this->nombre";
    }
}
$persona = new Persona();
$persona->nombre = "Arnau";
$persona->saludar();
```

---

## 4. Constructores y destructores

* **Constructor:** Se llama automáticamente al crear el objeto (`__construct`).
* **Destructor:** Se llama al destruir el objeto (`__destruct`).

```php
class Usuario {
    public $nombre;
    public function __construct($nombre) {
        $this->nombre = $nombre;
    }
    public function __destruct() {
        echo "Usuario destruido";
    }
}
$u = new Usuario("Pepe");
```

---

## 5. Visibilidad: public, private, protected

Controla el acceso a propiedades y métodos:

* **public:** Accesible desde cualquier lugar.
* **private:** Solo dentro de la clase.
* **protected:** Dentro de la clase y sus hijas.

```php
class Demo {
    public $pub = "público";
    private $priv = "privado";
    protected $prot = "protegido";

    public function verPrivado() {
        return $this->priv;
    }
}
$demo = new Demo();
echo $demo->pub;
// echo $demo->priv; // ERROR
// echo $demo->prot; // ERROR
echo $demo->verPrivado();
```

---

## 6. Herencia

Una clase puede heredar propiedades y métodos de otra.

```php
class Animal {
    public function saludar() {
        echo "Hola";
    }
}
class Perro extends Animal {
    public function ladrar() {
        echo "Guau";
    }
}
$p = new Perro();
$p->saludar();
$p->ladrar();
```

---

## 7. Sobrescritura de métodos

Una clase hija puede redefinir (sobrescribir) un método de la clase padre.

```php
class Animal {
    public function sonido() {
        echo "Sonido genérico";
    }
}
class Gato extends Animal {
    public function sonido() {
        echo "Miau";
    }
}
$g = new Gato();
$g->sonido();
```

---

## 8. Palabra clave static

Permite acceder a métodos o propiedades sin instanciar la clase.

```php
class Util {
    public static function sumar($a, $b) {
        return $a + $b;
    }
}
echo Util::sumar(3, 5);
```

---

## 9. Constantes de clase

Se definen con `const` dentro de la clase.

```php
class Mat {
    const PI = 3.1416;
}
echo Mat::PI;
```

---

## 10. Clases abstractas

Una **clase abstracta** no se puede instanciar directamente, solo sirve como base para otras clases. Puede tener métodos abstractos (sin cuerpo) que deben implementarse en las clases hijas.

```php
abstract class Figura {
    abstract public function area();
}
class Cuadrado extends Figura {
    public $lado;
    public function __construct($lado) {
        $this->lado = $lado;
    }
    public function area() {
        return $this->lado * $this->lado;
    }
}
$c = new Cuadrado(4);
echo $c->area();
```

---

## 11. Interfaces

Una **interfaz** define qué métodos debe tener una clase, pero no su implementación. Una clase puede implementar varias interfaces.

```php
interface Movible {
    public function mover($distancia);
}
class Robot implements Movible {
    public function mover($distancia) {
        echo "Moviendo $distancia metros";
    }
}
$r = new Robot();
$r->mover(5);
```

---

## 12. Polimorfismo

Permite usar diferentes clases de manera intercambiable si implementan la misma interfaz o heredan de la misma clase base.

```php
function hacerSonido(Animal $animal) {
    $animal->sonido();
}
hacerSonido(new Gato()); // Miau
```

---

## 13. Traits

Los **traits** permiten reutilizar métodos en varias clases (como “módulos” que se pueden mezclar).

```php
trait Mensajero {
    public function enviarMensaje($msg) {
        echo "Mensaje: $msg";
    }
}
class Usuario {
    use Mensajero;
}
$u = new Usuario();
$u->enviarMensaje("Hola");
```

---

## 14. Ejemplo práctico completo

```php
interface Figura {
    public function area();
}
class Circulo implements Figura {
    private $radio;
    public function __construct($radio) {
        $this->radio = $radio;
    }
    public function area() {
        return 3.1416 * $this->radio * $this->radio;
    }
}
$figuras = [new Circulo(2), new Cuadrado(3)];
foreach ($figuras as $fig) {
    echo $fig->area() . "<br>";
}
```

---

## 15. Errores comunes

* Olvidar implementar todos los métodos de una interfaz.
* Intentar instanciar una clase abstracta.
* No usar `parent::` cuando quieres llamar al método del padre.
* Olvidar `use` al emplear un trait.
* Acceder incorrectamente a visibilidad (public/private/protected).

---

## 16. Recursos para practicar

* [W3Schools: PHP OOP](https://www.w3schools.com/php/php_oop_what_is.asp)
* [Manual PHP - Clases y objetos](https://www.php.net/manual/es/language.oop5.php)
* [Manual PHP - Traits](https://www.php.net/manual/es/language.oop5.traits.php)