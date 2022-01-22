# Què utilitzar i que no?

![image](https://user-images.githubusercontent.com/4015406/150647979-a945799f-8328-46da-8018-015f2c6a28da.png)

NO UTILITZAR?
- Local Storage: Limitat a String, limitat en mida (Ionic storage plugin utilitza primer IndexedDB)
- Web SQL: El suport ha estat eliminat a múltiples navegadors. Migrar a IndexedDB
- Session Storage -> ús molt limitat
- Cookies: s'utilitzen per a sessions i altres formes de tracking (publicitat). S'envien com a capçaleres en cada petició HTTP, per tant si emmagatzement grand quantitats de dades afecten al rendiment.
- **SEGURETAT**: cap ni un dels sistemes al tractar-se de sistemes **client side** es poden utilitzar per guardar dades sensibles. nota: oco però que se suposa que al ordinador d'una persona ja hi ha moltes dades sensibles propies d'aquella usuari/persona i en cas de ser hackejat els problemes que pot tenir segurament van més enllà. Per exemple no guardar dades de altres usuaris o dades sensibles en general es una bona pràctica (cal fer-ho al backend). Guardar però tokens temporals és una pràctica habitual.

Que utilitzar depenent de? 

Recursos de l'aplicació (.js, .css, .html, imatges i altres assets)
- Són relativament estàtics: són estàtics per a una versió de lcodi. Només canviar quan hi ha una versió nova -> Només són problema pels desenvolupadors -> Distribució versions noves.
- Utilitzar **Cache Storage API** (part dels service workers)

Per a tota la resta:
- **indexedDB** (with a promises wrapper).

Recursos
- https://web.dev/storage-for-the-web/

# How much can I store?

Lo més habitual? Molt, des de centenars de megabytes a fins i tot gygabites però depén de l'espai disponible del disc dur del client.

- **Chrome**: Fins 80% of total disk space. Un sol origin 60% . SotrageManager API permet consultar com està l'espai
- **Internet Explorer 10** and later can store up to 250MB and will prompt the user when more than 10MB has been used.
- Firefox allows the browser to use up to **50% of free disk space**

# Eviction (desallotjament de l'espai)

Tots els sistemes Storage són "Best Effort". Vold dir que el navegador farà tot el possible per mantenir les dades però si es veu apurar d'espai és lliure d'alliberar espai sense interrompe l'usuari. Per tant no podem comptar en el fet que les dades estiguin smepre disponibles.

HI ha però un permís que es pot solicitar a l'usuari per tal que les dades persisteixin sempre i només s'esborrin si l'usuari ho demana explícitament.

https://caniuse.com/?search=persistent

![image](https://user-images.githubusercontent.com/4015406/150648622-83ba6f5c-58d6-4079-8663-265ac6ee8d0e.png)

# IndexedDB

IndexedDB és una API low level per a client-side storage. Té suport per a múltiples estructures de dades incloent fitxers de qualsevol tipus. 

**NOTA**: és una api complicada amb una corba aprenentatge alta al ser de "low level". Es poden utilitzar múltiples llibreries per fer-ho més fàcil. Amb Ionic utilitzem [Storage api](https://github.com/ionic-team/ionic-storage).

Recursos:
- https://developer.mozilla.org/en-US/docs/Web/API/IndexedDB_API

## idb

Vídeo explicatiu:

https://www.youtube.com/watch?v=VNFDoawcmNc&list=PLNYkxOF6rcIB2xHBZ7opgc2Mv009X87Hh&index=36

Recursos:
- https://www.npmjs.com/package/idb
- https://www.youtube.com/watch?v=VNFDoawcmNc&list=PLNYkxOF6rcIB2xHBZ7opgc2Mv009X87Hh&index=36
# Recursos

- https://web.dev/storage-for-the-web/
