# Notes

Què és? https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview

![image](https://user-images.githubusercontent.com/4015406/138273490-8bb5868e-9bef-4553-83d9-f28c314b1f7d.png)

![image](https://user-images.githubusercontent.com/4015406/138273564-164a4367-1ead-490b-8f94-be36540271f4.png)

![image](https://user-images.githubusercontent.com/4015406/138273869-6ea67d98-4010-4df8-984e-6e5e366bfb0e.png)
https://www.freecodecamp.org/news/http-and-everything-you-need-to-know-about-it/

![image](https://user-images.githubusercontent.com/4015406/138273302-3341e84f-3365-46c1-8df4-30bd34995a96.png)


- Coneixements previs: URL: https://en.wikipedia.org/wiki/URL
- Per dominar al nivell màxim caldira llegir les specs: https://url.spec.whatwg.org/
- RFC -> Request For Comments -> pq estan obertes a discusions i realitzats per experts
- Ho porta la Internet Engineering Task Force
- Inventat per Tim Berners-Lee al 1991 -> Base de la WWW -> Protocols HTTP, HTML i URLs
- HTTP: https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol
- Inicials del nom -> HyperText_Transfer_Protocol
- Protocol per transferir documents HTML -> inicialment -> Ara suporta moltes més opcions
- Client Server Model
- Servidors HTTP: Nginx, Apache, http-server, php -S, entorns de desenvolupament npm run dev, 
- Clients HTTP: telnet, navegadors web, clients per CLI httpi, curl, wget, el propi llenguatge php suporta descarregar fitxers via HTTP
- Protocol basat en text i per missatges. Dos tipus de missatges

Missatges
- HTTP REQUEST
- HTTP RESPONSE

Parts d'un paquet HTTP
- Capçalera/Headers
- Línia en blanc
- Contingut (sol ser un HTML) però pot ser qualsevol tipus de fitxers

Exemples:

https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/Evolution_of_HTTP

HTTP per a documents que no siguin HTML -> MimeType

REQUEST
https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol#Request_messages
- Request syntax
- User Agent
- REQUEST METHODS https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol#Request_methods

RESPONSE
https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol#Response_messages
- Response Syntax
-STATUS CODES
  - 200
  - 300

Eines:
- telnet -> Repàs xarxes connexió via socket TCP/IP
- Navegadors web: Chrome defveloper Tools F12 pestanya Network
- Client HTTP inclòs a PHPStorm
- Plugins browser -> POSTMAN
- CLI: curl, web, HTTP pie

# URL 

Vegeu:
- https://en.wikipedia.org/wiki/URL

Una adreça URL té la finalitat d’accedir a un recurs en un servidor.
Totes les adreces URL tenen diferents parts; agafem com a exemple

Exemple:

- **Protocol**: s’indica abans de :// i en aquest cas és HTTP. Hi ha altres
protocols, com ara FTP o HTTPS. Protocols El navegador utilitza el protocol
HTTP sobre TCP/IP perdemanar recursos (URL) als servidors web.
- **Adreça del servidor**: el lloc d’on es vol obtenir el recurs.
- **Port**: el port del servidor destinat a l’aplicació encarregada de gestionar les
peticions HTTP (port del servidor web). En cas de que no estigui especificat
es fa servir el port estàndard per HTTP (el port 80).
- **Ruta fins al recurs**: correspon a la ruta a la carpeta dins del servidor web
on es troba el recurs (educacio/fp-cicles-formatius/cfgs/).
- **Recurs**: és el recurs o fitxer que demanem al servidor (index.html).

El que primer fa el navegador és comunicar-se amb un servidor de noms per obtenir l’adreça IP que correspon al nom de la màquina ioc.xtec.cat. Amb aquesta IP es
connecta a la màquina servidor. A continuació, el navegador crea una connexió amb l’adreça IP del servidor al port 80, que és el port utilitzat per defecte en els
servidors web. Una vegada el client i el servidor estan connectats, “parlen” fent servir el protocol HTTP per tal que el client indiqui quins recursos vol del servidor. El servidor enviarà aquests recursos al client a través de la connexió establerta.

# HTTP

![image](https://user-images.githubusercontent.com/4015406/137494778-16c71211-4f3a-4070-bf7e-44236b6aeeb8.png)


## Servidors HTTPS


**Desenvolupament**:
- http-server: instal·lable amb node.js
- Laravel valet
- Laravel Sail -> Docker instance

**Explotació**:
- nginx
- Apache

# Recursos
- https://ioc.xtec.cat/materials/FP/Recursos/fp_asx_m09_/web/fp_asx_m09_htmlindex/media/fp_asix_m09_u1_pdfindex.pdf
