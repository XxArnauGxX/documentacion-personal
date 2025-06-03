# 13. Eventos y Queues en Laravel

---

## 1. ¿Qué es un evento en Laravel?

Un **evento** es una señal que indica que algo importante ha ocurrido en la app (por ejemplo: usuario registrado, pedido realizado, correo enviado). Los eventos permiten desacoplar la lógica, haciendo que ciertas acciones se ejecuten sólo cuando suceda algo.

---

## 2. ¿Qué es un listener?

Un **listener** (escuchador) es una clase que “escucha” eventos concretos y ejecuta código cuando ocurre ese evento. Así puedes separar la lógica principal de acciones secundarias (por ejemplo: enviar email al registrarse un usuario).

---

## 3. Crear un evento y un listener

Crear un evento:

```bash
php artisan make:event PedidoRealizado
```

Crear un listener:

```bash
php artisan make:listener EnviarEmailPedido --event=PedidoRealizado
```

Registrar ambos en `EventServiceProvider` (Laravel lo hace solo si usas los comandos artisan modernos).

---

## 4. Disparar un evento

En tu código:

```php
use App\Events\PedidoRealizado;

PedidoRealizado::dispatch($pedido);
```

---

## 5. Queues (colas de trabajo)

Las **queues** permiten ejecutar tareas “en segundo plano”, para que el usuario no tenga que esperar (por ejemplo: enviar correos, procesar imágenes, generar PDFs).

---

## 6. Crear un job para la queue

```bash
php artisan make:job ProcesarPedido
```

En el método `handle()` defines qué hace el job. Para lanzar el job:

```php
ProcesarPedido::dispatch($pedido);
```

Puedes hacer que un listener se ejecute en queue añadiendo la interfaz `ShouldQueue`:

```php
class EnviarEmailPedido implements ShouldQueue { ... }
```

---

## 7. Configuración básica de queues

* Elige el “driver” de queue en `.env` (`QUEUE_CONNECTION=database`, `redis`, `sync`, etc).
* Corre el worker en consola:

```bash
php artisan queue:work
```

Puedes ver jobs pendientes con:

```bash
php artisan queue:failed
```

---

## 8. Ejemplo completo (flujo típico)

1. Usuario hace una compra (PedidoRealizado::dispatch)
2. Listener EnviarEmailPedido recibe el evento
3. El listener se ejecuta en una queue, manda un correo y registra en logs
4. El usuario NO espera por ese proceso, respuesta rápida

---

## 9. Buenas prácticas

* Usa eventos para separar lógica principal y secundaria.
* Usa queues para procesos lentos o que no afecten a la respuesta inmediata.
* Asegura que tienes un sistema para manejar jobs fallidos.
* No abuses de queues para todo: usa solo cuando es necesario.

---

## 10. Errores comunes de principiante

* Olvidar arrancar el worker (`queue:work`), los jobs no se ejecutan.
* No registrar listeners o eventos en el EventServiceProvider.
* Meter lógica crítica en queues (si falla, el usuario no se entera).

---

## 11. Recursos para profundizar

* [Documentación oficial: Eventos](https://laravel.com/docs/events)
* [Documentación oficial: Queues](https://laravel.com/docs/queues)
* [Laracasts: Events & Listeners](https://laracasts.com/series/laravel-8-from-scratch/episodes/24)