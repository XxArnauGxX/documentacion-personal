# 14. Notificaciones y Mails en Laravel

---

## 1. ¿Qué es una notificación en Laravel?

Una **notificación** es un mensaje que tu aplicación envía a un usuario a través de distintos canales: email, base de datos, SMS, Slack, etc. Laravel facilita el envío de notificaciones de manera centralizada y reutilizable.

---

## 2. Enviar una notificación básica por email

1. Crear la notificación:

   ```bash
   php artisan make:notification PedidoEnviado
   ```
2. En la clase generada (`app/Notifications/PedidoEnviado.php`):

   ```php
   public function via($notifiable)
   {
       return ['mail'];
   }

   public function toMail($notifiable)
   {
       return (new MailMessage)
           ->subject('¡Tu pedido ha sido enviado!')
           ->line('Gracias por tu compra.')
           ->action('Ver pedido', url('/pedidos'));
   }
   ```
3. Enviar la notificación:

   ```php
   use App\Notifications\PedidoEnviado;
   $user->notify(new PedidoEnviado());
   ```

---

## 3. Notificaciones en base de datos

1. En el método `via`, añade `'database'`:

   ```php
   public function via($notifiable)
   {
       return ['mail', 'database'];
   }
   ```
2. Laravel guardará la notificación en la tabla `notifications`. Puedes consultar todas las notificaciones de un usuario con:

   ```php
   $user->notifications;
   $user->unreadNotifications;
   ```

---

## 4. Notificaciones por otros canales (Slack, SMS...)

Puedes añadir servicios como Slack, Nexmo, etc. Solo hay que añadirlos en el método `via` y configurar el canal correspondiente.

---

## 5. Enviar mails personalizados (Mailables)

Para mails más complejos que una notificación:

1. Crear un Mailable:

   ```bash
   php artisan make:mail FacturaEnviada
   ```
2. Edita la clase generada (`app/Mail/FacturaEnviada.php`) para configurar el contenido, vista y datos.
3. Enviar el mail:

   ```php
   use App\Mail\FacturaEnviada;
   use Illuminate\Support\Facades\Mail;

   Mail::to($user->email)->send(new FacturaEnviada($datos));
   ```

---

## 6. Enviar mails y notificaciones en colas (queues)

Si tu notificación o mail puede tardar, puedes enviarlo en una queue automáticamente:

* En la notificación, implementa la interfaz `ShouldQueue`.
* Asegúrate de tener el worker de la queue arrancado.

---

## 7. Configuración del correo en Laravel

En `.env`, configura los datos SMTP:

```
MAIL_MAILER=smtp
MAIL_HOST=smtp.mailtrap.io
MAIL_PORT=2525
MAIL_USERNAME=...
MAIL_PASSWORD=...
MAIL_ENCRYPTION=tls
MAIL_FROM_ADDRESS=info@tusitio.com
MAIL_FROM_NAME="Tu Sitio"
```

Puedes usar Mailtrap, Gmail, Sendgrid, Amazon SES, etc.

---

## 8. Buenas prácticas

* Usa notificaciones para avisos reutilizables y multicanal.
* Usa Mailables para mails complejos o personalizados.
* Envía mails y notificaciones largas por queue.
* No expongas datos sensibles en los mails.

---

## 9. Errores comunes de principiante

* No configurar correctamente SMTP y fallan los envíos.
* No implementar ShouldQueue para notificaciones/mails lentos.
* Olvidar leer/gestionar notificaciones en la base de datos.
* Repetir la misma lógica de notificación en muchos sitios (centraliza en clases).

---

## 10. Recursos para profundizar

* [Documentación: Notificaciones](https://laravel.com/docs/notifications)
* [Documentación: Mail](https://laravel.com/docs/mail)
* [Laracasts: Mails & Notifications](https://laracasts.com/series/laravel-8-from-scratch/episodes/25)