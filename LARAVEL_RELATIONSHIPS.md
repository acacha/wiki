# Screencasts

Vídeos:

- [132 Laravel Database Relationships. Relació 1 a n series i videos](https://youtu.be/VTIqo4fGkMs)
- [133 Més sobre relacions](TODO)

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
- published_at: null si no està publicada i la data de publicació si està publicada

La nostra funcionalitat principal es mostrar a la Landing page (https://casteaching.test/) però també al dashboard una llista de les series disponibles.

Recordeu us recomano sempre començar per la funcionalitat principal i no procastrinar, tenim múltiples codis per implementar:

- CRUD de series
- Modificar CRUD de vídeos per associar series a videos
- **Mostrar les series a la landing page**
- Afegir un sidebar a la visualització de vídeos que permeti veure tots els vídeos de la sèrie i navegar
- etc

Però de totes aquestes funcionalitat la principal és la tercera. Algú pot dir però? com podem mostrar una llista de series si no fem abans el CRUD que les permeti editar? Doncs creant uns seeds que de moment ens generin les series que desitgem a la base de dades i més endavant ja farem el crud

**Mostrar les series a la landing page**
- La landing page tindrà múltiples seccions
- La landing page actual és una pàgina estàtica, és de les primeres coses hem de canviar
- A https://tailwindui.com/ tenim multiples exemples de Landing pages i seccions
- Proposo que cada Serie tingui una card i podem utilitzar https://tailwindui.com/components/marketing/sections/blog-sections#component-720cf60b960fecb99c45f462f24db2d9
- Al fer click a la card es mostrarà el primer vídeo de la sèrie

![image](https://user-images.githubusercontent.com/4015406/150312237-5fa8c650-d881-4b53-8e58-fefd9a9fccd8.png)
 
 Especificacions:
 - Les sèries es mostren ordenades primer les més noves (data de creació)
 - La landing page la dividirem en components. Fem un component secció i el provem i creem de forma independent a la Landing Page
 - php artisan make:component CasteachingSeries
 - A app/View/Components estarà la classe PHP que podrem testejar i a resources/views/components la vista -> Separation of concerts
 - El test: php artisan make:test CasteachingSeriesTest
 - A la landing page només posarem el component amb <x-casteaching-series> . El prefix casteaching pot ser útil per evitar conflictes de noms (espai de noms)
 - Al test de la Landing Page només mirarem que el component es mostra
 - Testing de Views: https://laravel.com/docs/8.x/http-tests#testing-views
 - Testing de blade components: https://laravel.com/docs/8.x/http-tests#rendering-blade-and-components
 - Tothom (guests users) pot veure NOMÉS les series publicades 
 - Els usuaris administradors podran veure totes les series
 
Tests:
- HAPPY PATH: guest_users_can_see_published_series
- guest_users_cannot_see_unpublished_series
- regular_users_cannot_see_unpublished_series
- superadmin_users_can_see_all_series
 
 # Vídeo 133
 
 *Recopilació*
 - Error en la migració drop al copiar i pegar posava user_id en comptes de serie_id
 - Script de deployment: https://gist.github.com/acacha/9bd560e39de2fcb6f3f9d9592f1fd58d
 - Veure els últims commits: https://github.com/acacha/casteaching/commits/main
 - Error en la font -> Inter.css | https://github.com/acacha/casteaching/commit/f449f7cf554afd81fec129b3bc3caaf77be3a08b | npm run dev
 - Repassar fitxer .env a explotació dins de Laravel Forge
 ![image](https://user-images.githubusercontent.com/4015406/150671207-646fa7d5-a367-43fe-9d17-29fbbb74c318.png)

 Més sobre relacions:
 
 Relació inversa:
 - Obtenir la serie d'un vídeo | [Belongs to o one to many invers](https://laravel.com/docs/8.x/eloquent-relationships#one-to-many-inverse)
 - Adaptació de Laravel a qualsevol esquema de base de dades (els noms dels camps foreign keys es poden configurar, tot es configurable -> No recomano en aplicacions que creem des de zero )
 - Test TDD per a Video
 - [Com comptar el número de vídeos d'una serie](https://laravel.com/docs/8.x/eloquent-relationships#counting-related-models)
 - Opcional: temps total de la serie: sumar el temps de cada vídeo i obtenir un total
 - Actualitzar el CRUD de videos per poder afegir/editar la serie a https://casteaching.test/manage/videos . Component select. Primer TDD afegir testos
 - UI del select: https://tailwindui.com/components/application-ui/forms/select-menus
 - Exercidi: el mateix amb user_id | select amb avatars: https://tailwindui.com/components/application-ui/forms/select-menus#component-71d9116be789a254c260369f03472985
 Exercici api series amb TDD
 - Incloure o no incloure la llista de vídeos d'una serie dins de cada serie?
 - Actualitzar casteaching_package -> Altra serie
 - Actualitzar casteachingIonic per mostrar la llista de seires
 
 Laravel API resources
 - https://laravel.com/docs/8.x/eloquent-resources
 
# Recursos

- https://laravel.com/docs/8.x/eloquent-relationships
