# Screencasts

Vídeos:

- [132 Laravel Database Relationships. Relació 1 a n series i videos](TODO URL)

De la sèrie:

https://tubeme.acacha.org/tdd

# Guió

Amb TDD definim un nou model i una nova relació. Volem crear series. Una serie és una llista ordenada de vídeos.

Dades d'una serie:
- id
- title
- description
- image: un thuimbnail o imatge de la serie
- timestamps de Laravel
- teacher_name
- teacher_photo_url

La nostra funcionalitat principal es mostrar a la Landing page (https://casteaching.test/) però també al dashboard una llista de les series disponibles.

Recordeu us recomano sempre començar per la funcionalitat principal i no procastrinar, tenim múltiples codis per implementar:

- CRUD de series
- Modificar CRUD de vídeos per associar series a videos
- **Mostrar les series a la landing page**
- etc

Però de totes aquestes funcionalitat la principal és la tercera. Algú pot dir però? com podem mostrar una llista de series si no fem abans el CRUD que les permeti editar? Doncs creant uns seeds que de moment ens generin les series que desitgem a la base de dades i més endavant ja farem el crud

**Mostrar les series a la landing page**
- La landing page tindrà múltiples seccions
- La landing page actual és una pàgina estàtica, és de les primeres coses hem de canviar
- A https://tailwindui.com/ tenim multiples exemples de Landing pages i seccions
- Proposo que cada Serie tingui una card i podem utilitzar https://tailwindui.com/components/marketing/sections/blog-sections#component-720cf60b960fecb99c45f462f24db2d9

![image](https://user-images.githubusercontent.com/4015406/150312237-5fa8c650-d881-4b53-8e58-fefd9a9fccd8.png)
 
# Recursos

- https://laravel.com/docs/8.x/eloquent-relationships
