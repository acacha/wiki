Laravel's events provide a simple observer pattern implementation, allowing you to subscribe and listen for various events that occur within your application.

Event classes are typically stored in the app/Events directory, while their listeners are stored in app/Listeners. 

Don't worry if you don't see these directories in your application as they will be created for you as you generate events and listeners using Artisan console commands.

Events serve as a great way to decouple various aspects of your application, since a single event can have multiple listeners that do not depend on each other. For example, you may wish to send a Slack notification to your user each time an order has shipped. Instead of coupling your order processing code to your Slack notification code, you can raise an App\Events\OrderShipped event which a listener can receive and use to dispatch a Slack notification.

# TDD

Si comencem a disparar events al nostre codi ens pot passar que els listeners associats a aquests events no siguinb codi nostre o fins i tot executin codi de tercers o crides a apis externes provocant que els nostres tests executin codi no desitjat que ho bé pot fer fallar els nostres testos o fins i tot pitjor pot executar codi en producció i modificard bases de dades propies o de tercers (apis externes).

Per aquests casos existeix el concepte de Code Isolation o Test Isolation, és a dir assegurar-se que els testos només executin el codi que realment volem provar i no codis de tercers com per exemple Listeners.

**Concepte de mocking | Event Fake**

Laravel té suport via fakes (mentides) o mocking (burles). En general un fake o mock en testing es desactivar la execució dels events però sense deixar de tenir formes de comprovar que "s'ha disparat" el esdeveniment a nivell de codi tot i que realment no ho fem per evitar l'execució dels Listeners

```php
class ExampleTest extends TestCase
{
    /**
     * Test order shipping.
     */
    public function test_orders_can_be_shipped()
    {
        Event::fake();

        // Perform order shipping...

        // Assert that an event was dispatched...
        Event::assertDispatched(OrderShipped::class);

        // Assert an event was dispatched twice...
        Event::assertDispatched(OrderShipped::class, 2);

        // Assert an event was not dispatched...
        Event::assertNotDispatched(OrderFailedToShip::class);

        // Assert that no events were dispatched...
        Event::assertNothingDispatched();
    }
}
```

https://laravel.com/docs/8.x/mocking#event-fake


Recursos
- https://laravel.com/docs/8.x/mocking

# Exercicis a Casteaching

sOlid: Open to Extensión, closed to modification:

Com podem extendre/ampliar codi ja existent i que funciona sense que deixi de funcionar i fins i tot que l'haguim de modificar el mínim possible?
- Disparant events propis. VideoCRUD: VideoCreated | VideoUpdated | VideoDestroyed | VideoShowed
- TDD -> Crearem primers els testos amb Event:Fake i comprovarem s'executen 
- Es tant important separar els testos dels controladors com els propis controladors (CRUD videos) dels testos dels listeners i dels propis listeners. L'únic nexe unió entre controladors que disparen events i listeners ha de ser el registre a EventServiceProvider, per a la resta han de funcionar de forma independent.

Registre d'usuaris:
- Especificació 1: Events ja existents a Laravel. Nou Usuari afegit al sistema -> Assignar permisos per defecte

Enviament de notificacions (emails de moment)
- Explicació: com enviar emails/notificacions
- Especificació 1: enviar un email a una llista de admins (configuragles al fitxer config/casteaching.php) cada cop que es crea un nou Video. Event: VideoCreated, definir la dependència de l'event (Video injectat al constructor)


ActivityLog
- TODO
- https://github.com/spatie/laravel-activitylog

Relació 1 a n amb series
- serie_id nullable -> Millor suport migracions, permet crear videos no associats a cap serie
- Desplegable series al crear un vídeo
- Cal CRUD de series? -> Podem utilitzar seeder/factoria de moment per afegir unes series per defecte. CRUD de series quedarà com a TODO
- Definir model Serie
- A la Dashboard i a la Landing Page mostrar una llista de series com un grid de cards: seeders i factories


# Altres llenguatges

Tots els llenguatges de frontend que utilitzem s'utilitzen principalment per disenyar User Interfaces (UI). Les UI funcionen principalment amb el mateix patró Observer amb events i Listeners amb els seu handlers


## Javascript

### Vanilla

En la majoria de casos no creem Events, sinó que utilitzem els events ja existents associats a la interacció de l'usuari amb el Navegador/Browser.

**EVENTS INCRUSTATS a HTML**

```html
<element event='some JavaScript'>
``` 

```html
<button onclick="document.getElementById('demo').innerHTML = Date()">The time is?</button>
``` 

**addEventListener**

```html
<button>Change color</button>
```

```javascript
const btn = document.querySelector('button');

function random(number) {
  return Math.floor(Math.random() * (number+1));
}

btn.addEventListener('click', () => {
  const rndCol = `rgb(${random(255)}, ${random(255)}, ${random(255)})`;
  document.body.style.backgroundColor = rndCol;
});
```
Recursos
- https://www.w3schools.com/js/js_events.asp
- https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Events

### VueJs

Esdeveniments propis:

Un component pot disparar un esveniment

```javascript
this.$emit('close')
```
 
I el component pare el pot escoltar amb v-on:

```javascript
<component on:close="doSomething">
```

Entre components que no tinguin relació pare/fill s'utilitza un EventBus o Vuex

EventBus:

Exemple: https://www.youtube.com/watch?v=yYfuRKTiZfY

Em utilitzat els esdeveniments a mida i el concepte de EventBus (que és el mateix que proporciona Laravel un sistema per disparar events i escoltar-los a on vulguem del nostre codi via Event Facade)

<script>
import bus from "../bus";

export default {
    name: "Status",
    data () {
        return {
            show: false,
            message: ''
        }
    },
    created() {
        bus.$on('status',(message) => {
            this.message = message
            this.show = true
        });
    }
}
</script>

Recursos:
- https://github.com/acacha/casteaching/blob/main/resources/js/components/Status.vue
- https://v3.vuejs.org/guide/migration/events-api.html#event-bus
- https://blog.logrocket.com/using-event-bus-in-vue-js-to-pass-data-between-components/


Docs:
- https://vuejs.org/v2/guide/components-custom-events.html

Gestió de esveniments de UI

```javascript
<div id="example-2">
  <!-- `greet` is the name of a method defined below -->
  <button v-on:click="greet">Greet</button>
</div>
var example2 = new Vue({
  el: '#example-2',
  data: {
    name: 'Vue.js'
  },
  // define methods under the `methods` object
  methods: {
    greet: function (event) {
      // `this` inside methods points to the Vue instance
      alert('Hello ' + this.name + '!')
      // `event` is the native DOM event
      if (event) {
        alert(event.target.tagName)
      }
    }
  }
})
```

- https://vuejs.org/v2/guide/events.html
- https://vueschool.io/lessons/vuejs-user-events?friend=vuejs

### NodeJs

```javascript
const EventEmitter = require('events');

class MyEmitter extends EventEmitter {}

const myEmitter = new MyEmitter();
myEmitter.on('event', () => {
  console.log('an event occurred!');
});
myEmitter.emit('event');
``` 

- https://nodejs.org/docs/latest-v12.x/api/events.html

# Observer pattern

![image](https://user-images.githubusercontent.com/4015406/148737764-006aae07-87cb-4c64-9c93-a49bcdbc48cd.png)


# Conceptes

- Observer Pattern: The observer pattern is a software design pattern in which an object, named the subject, maintains a list of its dependents, called observers, and notifies them automatically of any state changes, usually by calling one of their methods. | https://en.wikipedia.org/wiki/Observer_pattern
- Event classes: **app/Events**. Són simples objectes/classes contenidores de dades (només contenen dades, cap lógica) amb les dades del event: nom del event i dades associades al event (dependencies injectades a través del constructor)
- Listeners:  **app/Listeners**: Contenen la lògica associada al que cal executar quan succeix un esdeveniment. Seguint el *Single Responsability Principle* se sol dividir en tasques diferents (múltiples listenets) totes les accions a realitzar quan succeix un esdeveniment,


# Coneixements previs

- Service Providers: App\Providers\EventServiceProvider

# Procediment

1. Crear i Registrar els events i els listeners
2. Disparar/Dispatch/Trigger events


# Comandes artisan

- php artisan event:generate
- php artisan event:list
- php artisan make:event
- php artisan make:listener

# Objectius, avantatges i inconvenients

- Els esdeveniments són molt útils per mantenir el codi net i SOLID, especialment evitar controladors FAT (gordos) que realitzin moltes tasques
- Sovint serveixen per organitzar el codi en tasques principals i tasques secundaries. Exemple: Registrar un usuari: la tasca principal es afegir l'usuari a la base de dades però també pot haver-hi tasques secundaries: enviar un email al usuari nou, enviar un email als administradors informant que hi ha un nou usuari, actualitzar estadístiques usuaris, etc.
- INCONVENIENT: Tracking i relacions entre codi: al separar el codi en múltiples fitxers (Listeners) a vegades pot ser complicat saber quin controladro o quin codi a executat el event que estem gestionant. Eines com Laravel Telescope o Debugbar, els logs, etc ens poden però ajudar a gestionar
- Recordeu que també és el sistema que s'utilitza en UI (User interfaces) per associar codi a esdeveniments de la UI (clicks, touchs, keyboard events, etc)
- També molt relacionat amb diagrames d'estat, cicles de vida i hooks (els hooks no són més que listeners que s'executen quan succeix un esdeveniment)

SOLID:
- Single Responsability Principle: separem en diferents listeners les múltiples tasques associades a un api endpoint, a una crida a una URL, etc
- Open To Extension Closed to modification: quan disparem un event estem permeten als programadors escoltar/enganxar-se(hook) a aquest event crearn listeners i registran-los al event. D'aquesta manera el nostre codi pot creixer (extension) sense modificar-lo. Cal que entengueu que el codi que NO es modificar és el controlador o codi que dispara el event, només modifiquem el EventServiceProvider (registre de Listeners). Sovint en molts codis es disparen event tot i que no s'escoltin només per donar la posibilitat a altres desenvolupadors de extendre el codi.

# RECURSOS

- https://laravel.com/docs/8.x/events
- https://laracasts.com/series/intermediate-laravel