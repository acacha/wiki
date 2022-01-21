![image](https://user-images.githubusercontent.com/4015406/150493618-9380ece8-4b5a-4e1d-8c95-818eb23aa076.png)

# Introducció

- **PWA**: Sigles de Progressive Web Apps

# Característiques:

![image](https://user-images.githubusercontent.com/4015406/150494269-e0fd8fc4-7574-4730-932f-c10341687f25.png)

10 característiques que ha de complir un PWA:

- **Progressive**: funciona per cada usuari independentment del navegador i la plataforma escollida - Work for every user, regardless of browser choice because they’re built with progressive enhancement as a core tenant.
Responsive - Fit any form factor, desktop, mobile, tablet, or whatever is next.
Connectivity independent - Enhanced with service workers to work offline or on low quality networks.
App-like - Use the app shell model to provide app-style navigations and interactions.
Fresh - Always up-to-date thanks to the service worker update process.
Safe - Served via TLS to prevent snooping and ensure content hasn’t been tampered with.
Discoverable - Are identifiable as “applications” thanks to W3C manifests and service worker registration scope allowing search engines to find them.
Re-engageable - Make re-engagement easy through features like push notifications.
Installable - Allow users to “keep” apps they find most useful on their home screen without the hassle of an app store.
Linkable - Easily share via URL and not require complex installation.

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

# What web can do today

https://whatwebcando.today/

## Avantatges vs aplicacions Natives

![image](https://user-images.githubusercontent.com/4015406/150493912-d4e76352-2de8-48a9-9d32-e3de2e5873b2.png)


# Recursos
- https://web.dev/progressive-web-apps/
- https://www.youtube.com/watch?v=SnWVlWPbOwA
- https://developers.google.com/web/ilt/pwa
- https://whatwebcando.today/
