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

Recursos:
- https://www.youtube.com/watch?v=DfFlBWCQjzA&list=PLNYkxOF6rcIB2xHBZ7opgc2Mv009X87Hh&index=2

### Google Analytics

Bounce rate

# Casteaching

## Fitxers de manifest

Recursos
- 

# What web can do today

https://whatwebcando.today/

## Avantatges vs aplicacions Natives

![image](https://user-images.githubusercontent.com/4015406/150493912-d4e76352-2de8-48a9-9d32-e3de2e5873b2.png)


# Recursos
- https://web.dev/progressive-web-apps/
- https://www.youtube.com/watch?v=SnWVlWPbOwA
- https://developers.google.com/web/ilt/pwa
- https://whatwebcando.today/