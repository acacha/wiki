![image](https://user-images.githubusercontent.com/4015406/150493618-9380ece8-4b5a-4e1d-8c95-818eb23aa076.png)

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

TODO fer proves!

Vegeu:

https://github.com/silviolleite/laravel-pwa

# What web can do today

https://whatwebcando.today/

## Avantatges vs aplicacions Natives

![image](https://user-images.githubusercontent.com/4015406/150493912-d4e76352-2de8-48a9-9d32-e3de2e5873b2.png)


# Recursos
- https://web.dev/progressive-web-apps/
- https://www.youtube.com/watch?v=SnWVlWPbOwA
- https://developers.google.com/web/ilt/pwa
- https://whatwebcando.today/
