# Screencast

- Video [127 Notificacions per email](https://youtu.be/8oAcBl63Pvg). Enviament d'una notificació a administradors informant que s'ha creat un vídeo nou. 
- Video [128 Events Laravel i TDD amb Mocking. Afegir funcionalitats a codi existent](https://youtu.be/AUWTpfH-M44). Afegir funcionalitat enviament email a codi existent amb codi net utilitzant events i Listeners. Com fer-ho amb TDD i com aillar els testos amb mocks i fakes.

De la sèrie [Laravel TDD](https://tubeme.acacha.org/tdd) | https://tubeme.acacha.org/tdd:

![image](https://user-images.githubusercontent.com/4015406/148790766-f9dc9d7b-5d1e-4031-97b9-217bea42fd86.png)


# Currículum

- UF2 del mòdul MP9 (Processos i Serveis):  UF2 és la UF de processos, separació del codi en multiples mòduls que es poden executar concurrenment o linealment.
  - Amb Laravel i PHP utilitzarem les Cues o Jobs
  - Abans però cal aprendre com funcionen els events per tal de mantenir el codi net
  - També necessitem aprendre a realitzar tasques que siguin potencialment llargues en el temps com utilitzar APIs de tercers o enviar emails/notificacions.

# Resum de passes

1. Crear branca on fer les proves de la nova funcionalitat
2. Crear la notificació de tipus email i provar-la via Tinker
3. Provar la notificació creant una comanda de consola Laravel. Fí del video 1
4. Vídeo 2. Crear via TDD el test per al Listener/Classe PHP que envia la notificació. Mocking i adaptació testos existents per isolar els testos.
6. Lligar el codi ja existent amb la nova funcionalitat utilizant el patró observació i els events de Laravel.
7. Un cop provada la nova funcionalitat fer un merge a main

# Comandes

Branca:

```bash
git checkout -b VideoCreatedNotification
...
# Desenvolupem funcionalitat i tornem a la branca principal i afegim els canvis un cop ens agraden
git checkout main
git merge --theirs VideoCreatedNotification
```

[Creació de la notificació](https://laravel.com/docs/8.x/notifications#generating-notifications):

```
php artisan make:notification VideoCreated
```

Si tinguessim clar que no necessitem la abstració de les notificacions (només implementarem/enviarem emails) [podriem utilitzar](https://laravel.com/docs/8.x/mail#generating-mailables)

```
php artisan make:mail VideoCreated
```

Ara cal crear la notificació, en aquest cas el email en si, segons:

 https://laravel.com/docs/8.x/notifications#mail-notifications
 
Es poden utilitzar emails preformats:

```
public function toMail($notifiable)
{
    $url = url('/invoice/'.$this->invoice->id);

    return (new MailMessage)
                ->greeting('Hello!')
                ->line('One of your invoices has been paid!')
                ->action('View Invoice', $url)
                ->line('Thank you for using our application!');
}
```

O podeu implementar la vista a mida:

```
public function toMail($notifiable)
{
    return (new MailMessage)->view(
        ['emails.name.html', 'emails.name.plain'],
        ['invoice' => $this->invoice]
    );
}
```

Com enviar la notificació, en el nostre cas utilitzarem la [Facade Notification](https://laravel.com/docs/8.x/notifications#using-the-notification-facade) (disponible gràcies al ServiceProvider de notificacions):

```
Notification::send($users, new InvoicePaid($invoice));
```

Però oco no volem users (que ja sabeu que a Laravel tots tenen email) sinó que utilitzarem directament emails, [On Demand Notifications](https://laravel.com/docs/8.x/notifications#on-demand-notifications):

```
Notification::route('mail', 'taylor@example.com')
            ->route('nexmo', '5555555555')
            ->route('slack', 'https://hooks.slack.com/services/...')
            ->notify(new InvoicePaid($invoice));
```

Inicialment podem fer un test Manual executant el codi a Tinker:

```
php artisan tinker
$video = create_sample_video();
Notification::route('mail', 'sergiturbadenas@gmail.com')->notify(new VideoCreated($video);
```

El seguent pas es fer ja un test real i aprofitar el TDD per crear la classe (Listener) Encarregat de lligar el codi

# Guió

**Nova funcionalitat**: **enviar emails formatats amb Markdown** cada cop que **es crea un nou vídeo**. La notificació per email s'envia a una **llista d'administradors configurable** (fitxer de configuració casteaching)

Intentem ja utilitzar bones pràctiques? El codi es començar a complicar a semblar més a la vida real -> Codi NO JUGUET. El problema dels exemples "Hello world" o exemples simples inicials és que tot i anar bé per començar, no representen un nivell real de coneixement intermig/avançat. Són exemples "Juget" / Toy examples

Necessitarem de patrons/paradigmes/exemples de formes de treballar per mantenir el codi net (Clean Code)

Llibre Amazon "Clean Code"  de Robert C. Martin "Uncle Bob": https://www.amazon.es/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882/ref=asc_df_0132350882/?tag=googshopes-21&linkCode=df0&hvadid=54582498915&hvpos=&hvnetw=g&hvrand=38037292843238465&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=9049225&hvtargid=pla-82950747900&psc=1

**SOLID**: Són les sigles d'una sèrie de tècniques/patrons/formes de treballar recomanables per mantenir el codi net (Clean Code)
- La S és Single Responsability Principle -> Focus
- La 0 de Open to Extensión / Closed to modification
- Liskov Substitution: Programació utilitzant interficies/contractes. Al canviar una classe per un altre no ha de donar problemes si compleixen el mateix contracte o interfície.
- Interface seggregation: Separar les intefícies/contractes complexes (amb molts mètodes) en interfíces més simples. Sempre podem implementar una classe que implmenti de cop múltiples interfícies. Més focus, més reaprofitables. Cap client ha de ser forçat a implementar mètodes que no utilitza. Múltiples interfícies concretes són millor que interfícies de proposit general
- Dependency Inversion: Decoupling modules (fent que els trossos de codi no siguin dependents entre ells). De fet sempre hi ha una dependencia però aquesta ha de ser basada en abstraccions (interficies | API) i no pas en implementacions concretes de forma que si canvio la implementació no deixi de funcionar el codi

Com no programar en projectes grans i que calgui mantenir nets?

- Cal vigilar molt al afegir noves funcionalitats
- Els testos ens ajuden a veure si les noves funcionalitats afecten al codi antic
- Però encara es pot anar més enllà, ja podem mirar de que cada cop que creem una nova funcionalitat compleixi SOLID. Podem mirar de posar-la en un tros de codi nou (mòdul és el concepte, en PHp i Laravel sovint una  o múltiples noves classes) i lligar el codi antic (mòdul/classe existent/controlador, etc) amb el codi nou utilitzant també SOLID -> minimitzar les dependències utitzant interfícies (API) i no pas implementacions concretes.

# Video 1

- Teòria bàsica sobre notificacions. Diferències entre Notificacions i emails. Notificació -> Abstracció/Api i email és una implementació concreta de la API de notificacions/abstracció. Lligar-ho amb solid
- Primer pas: crear un mòdul nou/classe PHP on afegir el codi nou de moment completament isolat/deslligat/decoupled (no acoblat) al codi antic
- Dos parts: 1 ) Crear la notificació Laravel 2) Executar-la . Haurem de decidir on executar? Ho podriem fer al controlador on es crea el video però recordeu: volem fer decoupling del codi

FUNCIONALITAT: Enviar email a una llista admins (llista de correus electrònics) notificant s'ha creat un nou vídeo

Com serà la API? Que cal definir?

**Nom de la classe i mètodes** -> Cal implementar alguna interfície

Noms de la classes: 

**Notificació**:
- VideoCreated: més que suficient
- Altres: VideoCreatedNotification <- no recomano. Notification No cal ja estarà a una carpeta notifications però a més implementarà una interfície
Mètode amb la lògica: podria ser send? però escolli un nom més genèric ja veurem més endavant pq -> handle

**Enviament de la notificació**
- SendVideoCreatedNotification
- A evitar: onVideoCreated, posar el nom listener a la classe tampoc cals
- Serà un Listener, ho veurem al pròxim vídeo (events Listeners)

Paràmetres entrada (dependències): que necessita la classe per funcionar 
- Video creat (objecte video) (injectat pel constructor)
- Llista de emails -> Aquí podem utilitzar valors hardcoded (accés via config() helper) no cal sigui dependencia

Paràmetres de sortida:
- Que retorna handle? en aquest cas no cal retornar res

Escribim el Test:



# Notifications vs Emails

Les notificacions són un concepte més global. Heu de veure els emails com un tipus de notificació. Els emails són un dels sistemes principals de notificar als usuaris i van ser el primer sistema de notificació, però actualment també podem utilitzar SMS, notificacions de broadcast en temps real i tot tipus de apis de tercers: Whatsapp, telegram, Webpush (notificacions mobils), VOIP, etc.

# Tasques Casteaching

Enviar email a administradors cada cop es crear un nou Video

Especificacions:
- Els receptors de la notificació via email són definits en un array de configuració a config/casteaching.php
- La notificació necessita/depèn i per tant cal injectar la dependència Video (objecte amb el video creat)
- Crearem un listener amb el seu propi handler que enviara la notificació
- La notificació de moment només serà de tipus email en format markdown
- Nom de la classe: SendShipmentNotification
- TDD: Test unitari?
- De moment no la farem un listener -> Ho farem més tard per passos

## Passos del test

**Preparació**
- Cal crear primer un video nou de prova
- Cal aconseguir via config - config('casteaching.admins') la llista de emails dels admins (https://laravel.com/docs/8.x/configuration#accessing-configuration-values) la llista de 
- Cal crear l'objecte SendShipmentNotification i injectar a través del constructor les dependències
- Notification:fake

**Execució**

Executar el metode handle() de SendShipmentNotification

**Comprovació**
- Comprovar que s'ha enviat la notificació als usuaris admins i que la notificació conté el video amb les dades adequades (title, url)

## Comanda artisan CLI per provar l'enviament de la notificació

Comandes artisan Laravel:

https://laravel.com/docs/8.x/artisan

Ens permeten executar codi des de la CLI (línia de comandes ) via php artisan laNostraComanda

Recordeu que per a fer proves sempre tenim la comanda php artisan tinker.

Crear la comanda:

php artisan make:command SendVideoCreatedNotificationTest

L'únic que ha de fer es crear el listener i executar-lo (igual que al test) creant un video de prova. Un cop creat el video i enviat el email, esborrar-lo.

## Que cal saber?

Notificacion Facade: https://laravel.com/docs/8.x/notifications#using-the-notification-facade

Exemple:

```
Notification::send($users, new InvoicePaid($invoice));
```

On:
- $users: problema no necessariament els admins han de ser usuaris, sinó una llista de emails

Utilitzarem https://laravel.com/docs/8.x/notifications#on-demand-notifications

```php
Notification::route('mail', 'taylor@example.com')
            ->route('nexmo', '5555555555')
            ->route('slack', 'https://hooks.slack.com/services/...')
            ->notify(new InvoicePaid($invoice));
```

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

# Vegeu també

- https://github.com/acacha/wiki/blob/main/LARAVEL_EVENTS.md

# Recursos

- https://laravel.com/docs/8.x/notifications
- https://laravel.com/docs/8.x/mail
