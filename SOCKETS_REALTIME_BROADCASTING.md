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

# Recursos
  
- https://laravel.com/docs/9.x/broadcasting
