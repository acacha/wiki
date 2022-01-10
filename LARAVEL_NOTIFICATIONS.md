# Notifications vs Emails

Les notificacions són un concepte més global. Heu de veure els emails com un tipus de notificació. Els emails són un dels sistemes principals de notificar als usuaris i van ser el primer sistema de notificació, però actualment també podem utilitzar SMS, notificacions de broadcast en temps real i tot tipus de apis de tercers: Whatsapp, telegram, Webpush (notificacions mobils), VOIP, etc.

# Tasques Casteaching

Enviar email a administradors cada cop es crear un nou Video

Especificacions:
- Els receptors de la notificació via email són definits en un array de configuració a config/casteaching.php
- La notificació necessita/depèn i per tant cal injectar la dependència Video (objecte amb el video creat)
- Crearem un listener amb el seu propi handler que enviara la notificació
- La notificació de moment només serà de tipus email en format markdown

**Que cal saber?**

Notificacion Facade: https://laravel.com/docs/8.x/notifications#using-the-notification-facade

Exemple:

```
Notification::send($users, new InvoicePaid($invoice));
```

On:
- $users: problema no necessariament els admins han de ser usuaris, sinó una llista de emails

Utilitzarem https://laravel.com/docs/8.x/notifications#on-demand-notifications

Notification::route('mail', 'taylor@example.com')
            ->route('nexmo', '5555555555')
            ->route('slack', 'https://hooks.slack.com/services/...')
            ->notify(new InvoicePaid($invoice));


# Canals de tercers

https://laravel-notification-channels.com/about/

# Code Isolation

Codi SOLID, aprendre a crear petites porcions de codi responsables d'una tasca concreta i isolar-les separar-les al màxim entre si. Utilitzarem Event/Listeners per connectar les tasques.

# TDD

Hi ha un Fake/Mocking per a notificacions. A més normalment les notificacions no les considerarem gairebé mai com el codi principal, sinó un codi secundari que s'executa via un event/listener (que a més més endavant serà un job) i per tant al test principal del controlador només calda fer fake de l'esdeveniment. Només cal fer fake de la notificació al test del listener

- https://laravel.com/docs/8.x/mail#testing-mailables
- https://laravel.com/docs/8.x/mocking#mail-fake
- https://laravel.com/docs/8.x/mocking#event-fake
- https://laravel.com/docs/8.x/mocking#notification-fake

# Recursos

- https://laravel.com/docs/8.x/notifications
- https://laravel.com/docs/8.x/mail
