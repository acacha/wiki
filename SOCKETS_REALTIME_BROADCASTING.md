# Introducció

En moltes aplicacions web modernes, els WebSockets s'utilitzen per implementar interfícies d'usuari actualitzades en temps real. 
Quan algunes dades s'actualitzen al servidor, normalment s'envia un missatge a través d'una connexió WebSocket per ser gestionat pel client. 
WebSockets ofereix una alternativa més eficient per consultar contínuament el servidor de la vostra aplicació per trobar canvis de dades que s'haurien de 
reflectir a la vostra interfície d'usuari.
  
Per exemple, imagineu que la vostra aplicació pot exportar les dades d'un usuari a un fitxer CSV i enviar-los-hi per correu electrònic. 
Tanmateix, la creació d'aquest fitxer CSV triga uns quants minuts, de manera que trieu crear i enviar el CSV per correu dins d'una tasca a la cua. 
Quan el CSV s'ha creat i enviat per correu a l'usuari, podem utilitzar la difusió d'esdeveniments per enviar un esdeveniment que rep el JavaScript de la 
nostra aplicació. Un cop rebut l'esdeveniment, podem mostrar un missatge a l'usuari que li ha enviat el seu CSV per correu electrònic sense que mai 
hagi d'actualitzar la pàgina.

# Websockets

http://acacha.org/mediawiki/Web_socket

https://os.alfajango.com/websockets-slides/#/

![image](https://user-images.githubusercontent.com/4015406/165041989-20db7beb-cd2e-4300-ae81-5ddf4c4e7f18.png)

Es tracta d'un nou protocol, per tal cal entendre que no utilitzem HTTP. Les URL seran:

![image](https://user-images.githubusercontent.com/4015406/165042165-84ee0a4b-88a9-49b8-81de-c5f8d450bcb2.png)

En cas de we socket segur serà wss.

El client que utilitzem seran els navegadors moderns que tots suporten el protocol: https://caniuse.com/?search=websocket

El servidor ja és un altre tema: tenim dos opcions:

1) Muntar un servidor propi: és el que s'anomena una solució que necessita d'infraestructura propia. Teniu molt bones eines Open Source que ho permeten com [laravel-websockets](https://github.com/beyondcode/laravel-websockets) o [soketi](https://docs.soketi.app/)
2) Utilitzar un servei SaaS que ens proporcioni el servei. Alguns dels serveis més coneguts són Pusher i Abbly

En el cas que ens ocupa (Laravel) tenim [múltiples opcions](https://laravel.com/docs/9.x/broadcasting#server-side-installation] que veurem més endavant al menys un cas.

## Socket.io

Tot i el ampli suport dels navegadors per a la especificació HTML5 websocket:

https://caniuse.com/?search=websocket

A la pràctica (igual que passa amb altres casos, per exemple fetch i axios) molts programadors utilitzen una llibreria anomenada socket.io

http://acacha.org/mediawiki/Socket.io#.YmZOk9BBwkI

Laravel Broadcasting i Laravel Echo utilitzen aquesta llibreria.
  
# Laravel Broadcasting

Per ajudar-vos a crear aquest tipus de funcions, Laravel facilita la "emissió" dels vostres esdeveniments Laravel del servidor mitjançant una connexió 
WebSocket. La difusió dels vostres esdeveniments Laravel us permet compartir els mateixos noms d'esdeveniments i dades entre la vostra aplicació Laravel 
del servidor i la vostra aplicació JavaScript del costat del client.

Els conceptes bàsics darrere de la difusió són senzills: els clients es connecten a canals amb nom a la interfície, mentre que la vostra aplicació Laravel emet esdeveniments a aquests canals a la part posterior. Aquests esdeveniments poden contenir qualsevol dada addicional que vulgueu posar a disposició del frontend.

# Casteaching

https://tubeme.acacha.org/tdd

- TODO link vídeo 145 i 146

Que volem implementar?

En dos fases:
- Enviar una notificació en temps real. Volem poder enviar missatges/notificacions als usuaris amb una UI com https://tailwindui.com/components/application-ui/overlays/notifications
- Convertir la notificació en una Push Notification utilitzant Progressive Web Apps (PWA), concretament missatges push amb Service Workers.

Coneixement previs:
- [Esdeveniments Laravel](https://laravel.com/docs/9.x/events#main-content)
- [Notificacions Laravel](https://laravel.com/docs/9.x/notifications)


## Guió

- Quina UI utilitzar https://tailwindui.com/components/application-ui/overlays/notifications
- Creació i configuració dels esdeveniments i Listeners necessaris
- Configuració de la abstracció Notification: Inicialment només implementarem una notificació tipus Push a navegador però en un futur potser també volem enviar Email o una notificació a un canal Telegram o qualsevol altre canal de comunicació. Si implementen una notificació o tindrem preparat.
- Com ho implementem -> Implementació general, en qualsevol pàgina intranet el usuari pot rebre la notificació. Per tant cal afegir-ho al layout
- Instal·lació i configuració de Laravel Broadcasting
- Proves inicials locals amb driver log
- Configuració del SaaS per enviar realment els events via Broadcasting

UI:
![image](https://user-images.githubusercontent.com/4015406/165044727-80c70f07-f65c-41b4-bd92-cb4e008d158d.png)

Quina notificació implementarem?

Mirarem de fer-la una mica general utilitzant un objecte que tindrà:
- Title: Títol de la notificació
- Description (opcional):Descripció
- Icona (opcional): serà el text del nom icona volem utilitzar de Tailwind UI

Tot i tenir un cas general implementarem un cas concret:
- Notificació: S'ha afegir un vídeo nou (Title del vídeo) a la sèrie (títol de la sèrie)

**Que necessitem a nivell de programació?**

Events Laravel

- Crear o **reaprofitar** un Event: VideoCreated
- Crear un Listener: **SendVideoCreatedNotification**
- Disparar event VideoCreated quan toca (ja ho hauria de tenir fet
- Configurar Listener SendVideoCreatedNotification per ser executat quan es crea VideoCreated
- Adaptar el esdeveniment VideoCreated per tal que sigui de tipus Broadcast. Documentació https://laravel.com/docs/9.x/broadcasting#defining-broadcast-events
- Ha d'implementar la interfície **ShouldBroadcast**: class ServerCreated implements ShouldBroadcast
- Ha d'implementar el mètode **broadcastOn**. Ha de tornar un canal públic (de moment no cal implementar missatges privats seran missatges que reben tots els usuaris). Utilitzeu doncs Channel **Illuminate\Broadcasting\Channel** en comptes de de PrivateChannel. El nom del canal: **notifications**

Repassem com ho fariem amb TDD, ja vam fer en vídeos anteriors treball amb esdeveniments:

- [Vídeo 128](https://youtu.be/AUWTpfH-M44)
- Cal afegir un test que s'asseguri que es disparà el esdeveniment quan toca. Utilitzem Mocks, Event:fake i assertDispatched Ja ho tenim fet a https://github.com/acacha/casteaching/blob/60bbf5694bc2c46f6c2487eec9663ffb72019cf6/tests/Feature/Videos/VideosManageControllerTest.php#L143
- Per tant la part del esdeveniment ja la teniu feta, només cal fer un nou Listener. O no? Ja en tenim un [**SendVideoCreatedNotification**](https://github.com/acacha/casteaching/blob/8ad7fcdc60aea6b944b23e0c6fe832f6765fd236/app/Listeners/SendVideoCreatedNotification.php#L10) l'únic que cal
 es que utilitzi el canal broadcast a part de canal email. Adapteu el [test SendVideoCreatedNotificationTest](https://github.com/acacha/casteaching/blob/f1407efd7fe5524c52c3011751e703dcfd436202/tests/Unit/SendVideoCreatedNotificationTest.php#L17)

Enrecordeu-vos que cada event porta un payload (com els paquets de qualsevol protocol) amb la info necessaria. En el nostre cas la info necessarìa serà 
l'objecte Video amb el vídeo que s'ha creat. Cal tenir en compte que cal que el objecte vídeo porti precarregat la relació serie amb la sèrie associada al vídeo. Per defecte Laravel fa Lazy Loading amb les relacions (no les porta carregades fins que no es necessiten) i les carrega quan les necessita. Però això només funciona en server side. Penseu que haurem de recuperar el vídeo al client un cop rebuda la notificació de broadcasting i per tant caldrà utilitzar Eager Loading al passar el objecte vídeo a l'esdeveniment VideoCreated.

Notificacions Laravel
- **Reaprofitar** la notificació: VideoCreated
- Afegiu un nou canal (a part del email) al mètode via. Consulteu els docs: [Especifying Delivery Channels](https://laravel.com/docs/9.x/notifications#specifying-delivery-channels)
- El nou típus canal és **broadcast**. Vegeu els docs https://laravel.com/docs/9.x/notifications#broadcast-notifications
- Cal implementar doncs el mètode **toBroadcast**

# Recursos
  
- https://laravel.com/docs/9.x/broadcasting
