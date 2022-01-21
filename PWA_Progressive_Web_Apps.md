![image](https://user-images.githubusercontent.com/4015406/150493618-9380ece8-4b5a-4e1d-8c95-818eb23aa076.png)

# Introducció

- **PWA**: Sigles de Progressive Web Apps

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
