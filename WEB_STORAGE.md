# Què utilitzar i que no?

![image](https://user-images.githubusercontent.com/4015406/150647979-a945799f-8328-46da-8018-015f2c6a28da.png)

NO UTILITZAR?
- Local Storage: Limitat a String, limitat en mida (Ionic storage plugin utilitza primer IndexedDB)
- Web SQL: El suport ha estat eliminat a múltiples navegadors. Migrar a IndexedDB
- Session Storage -> ús molt limitat
- Cookies: s'utilitzen per a sessions i altres formes de tracking (publicitat)

Que utilitzar depenent de? 

Recursos de l'aplicació (.js, .css, .html, imatges i altres assets)
- Són relativament estàtics: són estàtics per a una versió de lcodi. Només canviar quan hi ha una versió nova -> Només són problema pels desenvolupadors -> Distribució versions noves.
- Utilitzar **Cache Storage API** (part dels service workers)

Per a tota la resta:
- **indexedDB** (with a promises wrapper).

Recursos
- https://web.dev/storage-for-the-web/

# Recursos

- https://web.dev/storage-for-the-web/
