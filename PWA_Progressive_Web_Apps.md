![image](https://user-images.githubusercontent.com/4015406/150493618-9380ece8-4b5a-4e1d-8c95-818eb23aa076.png)

# Screencasts

Consulteu: https://tubeme.acacha.org/pwa

![image](https://user-images.githubusercontent.com/4015406/150947963-0f5b76c6-f24a-4a53-a200-8c0c2d415ab5.png)

Vídeos:
- [101. Introducció a les Progressive Web Apps(PWA)](https://youtu.be/2QIV9vtqPx0)
- [102. Seguretat. Activació de l'escriptació TLS i protocol HTTPS](https://youtu.be/jyu49Y6aswcL)

# Currículum

- UF2 Processos i UF3 Serveis del MP9 Processos i serveis de DAM. Els Service Workers són un tipus de Workers, és a dir processos/jobs que s'executen de forma asíncrona i a més també són Serveis/Dimonis, és a dir processos que s'executen sense UI i de forma permanent.
- UF1 Desenvolupament aplicacions mòbils del MP8 del mateix nom de DAM
- Tota la part Responsive també té sentit al MP7 UF1 Interfícies.

# Introducció

- **PWA**: Sigles de Progressive Web Apps

I per què les PWA?

Segons les [estadístiques](https://youtu.be/DfFlBWCQjzA):

![image](https://user-images.githubusercontent.com/4015406/150498883-2183bfab-60b7-4f30-a39f-9cf18137d552.png)

Pot semblar que implementar aplicacions web vs aplicacions natives es una perdua de temps no? El problema és:

![image](https://user-images.githubusercontent.com/4015406/150499171-50300de1-1aea-47dc-83a2-f6d264a27be8.png)

és a dir només les grans apps treuen rendiment d'aquestes estadístiques.

Amb PWA es mira de afegir les característiques que li faltes a les aplicacions web respecte les apps natives però amb tots els avantatges de la web:

![image](https://user-images.githubusercontent.com/4015406/150499422-6f4ceb94-d330-4663-baff-0421931a480f.png)


# Característiques:

![image](https://user-images.githubusercontent.com/4015406/150494269-e0fd8fc4-7574-4730-932f-c10341687f25.png)

10 característiques que ha de complir un PWA:

- **Progressive**: funciona per cada usuari independentment del navegador i la plataforma escollida 
- **Responsive**: S'adequa a cada tipus de dispositiu (desktop, mobile, tablet...) o form factor.
- **Connectivity independent**: s'adapta a la qualitat de la xarxa (UX, spinners, loading states) i fins i tot funciona (o no falla) en mode offline.
- **App-like**: utilitza el shell model per tal de proveir de navegació a l'estil de les aplicacions
- **Fresh**: sempre actualitzada (up to date)
- **Safe**: Utilitza TLS (https)
- **Discoverable**: són identificables com aplicacions gràcies als fitxers de manifest i són localitzables pels search engines (google) per millorar el seu SEO. Es poden compartir via un link i es pot accedir a continguts interiors de la app amb links directes.
- **Re-engageable**: facilita que els usuaris tornin o es recordin d'utilitzar l'aplicació via notificacions (**push notifications**).
- **Installable**: permet als usuaris mantenir les aplicacions més utils a les seves Homes o Desktops sense la necessitat de app stores.
- **Linkable**: es poden compartir via URLS i no requereixen d'instaladors.

## Icones

- https://cthedot.de/icongen/
- https://javascript.plainenglish.io/app-icons-in-a-pwa-8fb775207ad7
- https://www.pwabuilder.com/imageGenerator
- https://tools.crawlink.com/tools/pwa-icon-generator/
- 
## Progressive

Cal disenyar les nostres aplicacions web amb **programació defensiva** de forma que les característiques de la nostra aplicació que siguin incompatibles amb plataformes
o navegadors antics no siguin obligatories o en tot cas no impedeixen utilitzar l'aplicació o part de l'aplicació. En el pitjor del casos cal tenir en compte la UX 
(User experience) i mostrar errors sensibles a l'usuari. En cap cas l'aplicació pot fallar sense donar cap explicació.

Totes les llibreries noves es poden protegir amb codi que comprovi abans si la llibreria està disponible.

```javascript
if ('serviceWorker' in navigator) {
  // OPTIONAL CODE USING ServiceWorkers
} else {
  console.log('Your browser does not support Service Workers');
}
```

Un altre opció disponible són els polyfills, són llibreries que s'instal·len a la nostra aplicació afegint la funcionalitat que li falta al navegador/paltaforma. L'inconvenient 
dels polyfills es que fan creixer la mida de la nostra aplicació.

Recursos
- https://caniuse.com/

## HTTPS (TLS)

Vídeo: https://tubeme.acacha.org/https | https://youtu.be/jyu49Y6aswc

Activació en aplicacions de backend (llenguatges script com PHP):
- (Laravel Forge): es pot tant instal·lar el propi certificat com utilitzar Let's Encrypt per activar SSL amb un sol click
- Laravel Valet

Desenvolupament en local
- Localhost: no cal per a funcionar amb Service Workers
- Millor però no utilitzar localhost per problemes de cache i utilitzar fake domains com *.test

Altres temes relacionats amb la configuració de servidors web HTTP ja siguin locals (development) o en explotació (Nging i Apache)
- Evitar treballar amb localhost amb service workers: Al fer un cache es fa per a un scope, és a dir per a una URL. Si la URL és localhost:3000 o localhost:8080 o similar però cada cop executem una aplicació diferent a la mateixa URL podem tenir problemes amb les caches i el funcionament dels service workers.
- SPA (Vue amb vue-router i similars) i FC (Laravel) -> Requereix d'una configuració de rewrite o redirecció de totes les peticions cap a un fitxer principal sigui index.html (Vue-router i SPA) o index.php a Laravel
- Vue-cli solution

# Service workers

Screencasts:
- [103. PWA. Service Workers](https://youtu.be/fl6X7Nwv3EA)

**Guió**:

Propietats:
- Requereixen HTTPS, excepte en localhost
- De totes formes localhost es poc recomanable, pot donar problemes de cache -> Al reutilitzar adreces com localhost:3000 o localhost:8080 per múltiples apps. Solució: utilitzar Incognito mode o utilitzar dominis locals de test (elmeudomini.test o elmeudomini.local) similar al que fem amb Laravel valet o modificant fitxer /etc/hosts
- Són [web workers](https://developer.mozilla.org/en-US/docs/Web/API/Web_Workers_API/Using_web_workers). 
- Els workers no són res més que procesos independents del procés principal Javascript (el habitual que utilitzem per manipular el DOM i fer la UI i UX de la nostra app)
- Els workers s'utilitzen per executar processos costosos en temps com manipular fitxers, reproduir/processar audio/multimedia, etc. Similar als Jobs de Laravel i als Threads de Java o qualsevol altre técnica de programació concurrent amb qualsevol llenguatge.
- Com a web workers no tenen accés al DOM (objecte document) o dit d'un altre manera no es poden utilitzar directament per a manipular la UI (User Interface)
- Funcionen amb events. Un altre cop utilitzem els events com a sistema per comunicar dos procesos independents: (Web Worker/Service Worker) -> Main Javascript Proces (DOM). És a dir si un worker vol manipular ho ha de fer enviant un esdeveniment al procés principal i aquest ha d'escoltar i gestionar (handler) l'esdeveniment
- Que ès un servei?: Són software en execució (un procés) normalment de forma continuada i sense Interfície amb l'usuari, excepte la comunicació via Events (o el que és el mateix comunicació via un protocol). En Linux també anomenem Daemons.  Exemples : tots els servidors (serveixen serveis ;) com Apache/Nginx, DNS, DHCP, etc.
- Són la base de PWA ja que permeten suport offline=Cache+Proxy , Push Notifications i Background sync

Farem el codelab: https://developers.google.com/codelabs/pwa-training/pwa03--going-offline#0

**Cicle de vida**

![image](https://user-images.githubusercontent.com/4015406/151132341-84d61f77-fedc-44fa-b22f-f8c464aea0fb.png)
![image](https://user-images.githubusercontent.com/4015406/151133007-73100a82-a060-433f-a7c6-5f636b9c6bb4.png)

Recursos:
- https://developers.google.com/web/fundamentals/primers/service-workers/lifecycle

**Com treballar amb SW: Eines: Chrome DevTools i Lighthouse**

El cicle de treball serà el típic de prova error i anar iterant però per això necessitem eines que permetin depurar els Service Workers (Chrome dev tools les incorpora per defecte) i també utilitzarem els reports de Lighthouse com a eina per veure la llista de tasques (checklist) per a fer una app PWA.

**Registrar un SW**

```
if ('serviceWorker' in navigator) {
  window.addEventListener('load', function() {
    navigator.serviceWorker.register('/sw.js').then(function(registration) {
      // Registration was successful
      console.log('ServiceWorker registration successful with scope: ', registration.scope);
    }, function(err) {
      // registration failed :(
      console.log('ServiceWorker registration failed: ', err);
    });
  });
}
```

Codi explicat:
- Primer es comprova si el navegador (navigator) suporta serviceWorker. Vegeu (CanIUse Service Workers)[https://caniuse.com/?search=service%20worker]
- Només registrem service worker un cop s'ha carregat tot el document (event load) i esetiguin disponibles tots els assers
- Es registra el service worker com un fitxer extra: **sw.js** que s'ha de trobar a l'arrel del projecte
- El registre torna una promesa. Registre correcte -> then | Registre incorrecte-> Catch
- L'scope és molt important: és el domini i prefix de URLs que el service worker tindrà sota control. Recordeu que s'executen de forma continua i en segon terme com a serveis i per tant poden provocar problemes al tenir un SW executant-se per un domini tipus localhost:3000 d'una anterior aplicació i reaprofitar el domini per a un altre aplicació.

**Offline example by hand**

Vegeu https://developers.google.com/codelabs/pwa-training/pwa03--going-offline#3 i | https://www.youtube.com/watch?v=dXuvT4oollQ&list=PLNYkxOF6rcIB2xHBZ7opgc2Mv009X87Hh&index=4&t=4s

Recursos:
- https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API
- https://developers.google.com/web/fundamentals/primers/service-workers
- https://developers.google.com/codelabs/pwa-training/pwa03--going-offline#0

## Rendiment / Velocitat

[Bounce rate/ Taxa de rebot](https://ca.wikipedia.org/wiki/Taxa_de_Rebot): és un terme de màrqueting d'Internet utilitzat per l'anàlisi de trànsit web. Representa el percentatge de visitants que entren al web i llavors marxen ("reboten") en lloc de continuar veient altres pàgines dins el mateix. La Taxa de Rebot es calcula segons el temps que una persona està dins la pàgina.

![image](https://user-images.githubusercontent.com/4015406/150500056-023948ae-7795-4249-9f4f-8c63233fc82c.png)

Una eina útil que incorpora Chrome Developer Tools és Ligthouse:

![image](https://user-images.githubusercontent.com/4015406/150505654-9d9cfbe3-fac3-4c5d-a38d-e71411bb86e9.png)


Recursos:
- https://www.youtube.com/watch?v=DfFlBWCQjzA&list=PLNYkxOF6rcIB2xHBZ7opgc2Mv009X87Hh&index=2


### Google Analytics

Bounce rate

# Casteaching

Seguirem les indicacions de lighthouse i la PWA checklist:

https://web.dev/pwa-checklist/

## Seguretat HTTPS

- **Local development**: valet secure
- **Production**: Laravel Forge instal·la automàticament utilitzant Let's Encrypt.

## Register a service worker

- Error: **Does not register a service worker that controls page and start_url**

Passos a seguir:

Al fitxer resources **resources/js/app.js**
```
if ('serviceWorker' in navigator) {
    window.addEventListener('load', () => {
        navigator.serviceWorker.register('/sw.js').then( reg => {
            console.log('SW Registered!', reg);
        }).catch(error => {
            console.log('Registration failed:',error);
        })
    })
}
```

Creeu el fitxer **public/sw.js**:

```
// TODO
```

Ara es queixarà que cal crear el fitxer manifest. Vegeu el seguent apartat.

Recursos
- https://web.dev/service-worker/?utm_source=lighthouse&utm_medium=devtools
- https://www.youtube.com/watch?v=dXuvT4oollQ&list=PLNYkxOF6rcIB2xHBZ7opgc2Mv009X87Hh&index=4

## Offline

- https://www.youtube.com/watch?v=dXuvT4oollQ&list=PLNYkxOF6rcIB2xHBZ7opgc2Mv009X87Hh&index=4

## Fitxers de manifest. Fent la nostra aplicació web instal·lable a la Home/Desktop Screen

Amb aquesta acció millorarem la integració de la nostra aplicació al SO que utilitza l'usuari i també millorarem el re-engage.

![image](https://user-images.githubusercontent.com/4015406/150511213-66136554-a2e6-49ea-861d-cd9e49bf2635.png)

Afegiu la línia (a la secció head de HTML) de cada layout (**resources/views/layouts**) fitxers app|casteaching|guest.blade.php

```html
<link rel="manifest" href="/manifest.json">
```

També aprofiteu i afegim les meta que pertoquin i altres capçaleres:

```html
        <meta name="theme-color" content="#FF0000">

{{--        Apple touch icon https://developer.apple.com/library/archive/documentation/AppleApplications/Reference/SafariWebContent/ConfiguringWebApplications/ConfiguringWebApplications.html--}}
        <link rel="apple-touch-icon" href="touch-icon-iphone.png">
        <link rel="apple-touch-icon" sizes="152x152" href="touch-icon-ipad.png">
        <link rel="apple-touch-icon" sizes="180x180" href="touch-icon-iphone-retina.png">
        <link rel="apple-touch-icon" sizes="167x167" href="touch-icon-ipad-retina.png">
```

A **public/manifest.json** poseu:

```
{
    "name": "Casteaching",
    "shortname": "Casteaching",
    "icons": [
        {
            "src": "icon-512x512.png",
            "sizes": "512x512",
            "type": "image/png",
            "purpose": "any maskable"
        }
    ],
    "start_url": "/",
    "display": "standalone",
    "orientation": "portrait",
    "background_color": "#FF0000",
    "theme_color": "#FF0000"
}
```

Al final ens interesa que el report de lighthouse doni:

![image](https://user-images.githubusercontent.com/4015406/150515577-b1882bf3-d084-4be3-b458-2bfa8ad93886.png)


Recursos
- https://web.dev/service-worker/?utm_source=lighthouse&utm_medium=devtools
- https://www.youtube.com/watch?v=dXuvT4oollQ&list=PLNYkxOF6rcIB2xHBZ7opgc2Mv009X87Hh&index=4
- https://www.youtube.com/watch?v=LWRdBywm4Zo&list=PLNYkxOF6rcIB2xHBZ7opgc2Mv009X87Hh&index=5

## Instalable. A2HS (Add to home Screen)

- https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Add_to_home_screen

## Offline support

Una tècnica possible és que el service worker mostri una URL especial (/offline per exemple) que prèviament ha estat cacheada.

```javascript
// Serve from Cache
self.addEventListener("fetch", event => {
    event.respondWith(
        caches.match(event.request)
            .then(response => {
                return response || fetch(event.request);
            })
            .catch(() => {
                return caches.match('offline');
            })
    )
});
```

TODO fer proves! Es pot combinar amb laravel-export (no va) o potser https://github.com/reelcms/static o https://jigsaw.tighten.co/

Vegeu:

https://github.com/silviolleite/laravel-pwa

# Laravel Static (laravel-export | reelcms package)

https://github.com/spatie/laravel-export | https://github.com/reelcms/static | https://jigsaw.tighten.co/

# What web can do today

https://whatwebcando.today/

## Avantatges vs aplicacions Natives

![image](https://user-images.githubusercontent.com/4015406/150493912-d4e76352-2de8-48a9-9d32-e3de2e5873b2.png)


# Recursos
- https://www.youtube.com/playlist?list=PLNYkxOF6rcIB2xHBZ7opgc2Mv009X87Hh
- https://web.dev/progressive-web-apps/
- https://www.youtube.com/watch?v=SnWVlWPbOwA
- https://developers.google.com/web/ilt/pwa
- https://whatwebcando.today/
