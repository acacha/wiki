![image](https://user-images.githubusercontent.com/4015406/139868779-d929922d-f2a0-4ae2-8f06-e2eb3c9dbf4f.png)


# Temes currículars que tractarem

- MP9 UF1: Seguretat. Accés a recursos publicats o no publicats, usuaris registrats i no registrats, autoritzacions (subscriptors)
- MP7 UF2: TDD, testos manuals i testos automàtics

# Llista de reproducció Youtube

https://tubeme.acacha.org/tdd | https://www.youtube.com/playlist?list=PLyasg1A0hpk07HA0VCApd4AGd3Xm45LQv

# Notes vídeos

## 101 Primer vídeo. Introducció

Link: https://youtu.be/ednlsVl-NHA

- Learning by doing: https://en.wikipedia.org/wiki/Learning-by-doing
- Laravel: El framework que utilitzarem
- TDD: Test Driven Development
- Mockup/Wireframe: maqueta o prototip del que volem realitzar. Existeixen al mercat múltiples eïnes per realitzar aquest prototips.
- /video_mockup
- Markdown: Format wiki utilitzat per Github i posiblement el format wiki més utilitzat en programació en l'actualitat (2021)
- Github Sponsors:
- Pàgines web estàtiques
- SaaS: Software as a Service. https://en.wikipedia.org/wiki/Software_as_a_service is a software licensing and delivery model in which software is licensed on a subscription basis and is centrally hosted.[2][3] SaaS is also known as "on-demand software" and Web-based/Web-hosted software.[4]
- CRUD: Create Retrieve Update Delete: Acrònim per recordar les operacion més habituals amb recursos.
- Focusing on the value -> No sempre el CRUD és el més important

Llista de tasques:
- TODO posar aquí


Codi/Commit:
- https://github.com/acacha/casteaching/tree/896eceac9f0e1d584c8d36c4a4371142e737705d

## 102 Segon vídeo. Creació del projecte Laravel i repositori Github

Link: https://github.com/acacha/casteaching

NOTES: S'acaba bruscament i alguna edició extra que caldria afegir.

Links als materials, apunts wiki:
- https://github.com/acacha/wiki/blob/main/casteaching.md
Links a recursos
- TDD by Adam Wathan: https://course.testdrivenlaravel.com/
- Adam Wathan: https://adamwathan.me/
- TDD Laracasts: https://laracasts.com/series/build-a-laravel-app-with-tdd
- TailwindCSS: https://tailwindcss.com/
- Tailwind UI: https://tailwindui.com/
- Acacha_dev: https://youtube.acacha.org
- Repositori Github: https://github.com/acacha/casteaching

Eines necessàries:
- Laravel instal·lat: https://tubeme.acacha.org/101
- Github CLI: https://cli.github.com/
- PHPStorm: Instal·lar segons vídeo 101 amb Toolbox app de Jetbrains: https://www.jetbrains.com/toolbox-app/

Petit tall: EDITAR -> TODO

Comandes:

```bash
cd ~/Code
cd acacha
laravel new casteaching
```

I podeu veure els passos que cal per crear repositori Github amb l'ajuda que ens dona quan teniu un repositori buit, Exemple:

https://github.com/acacha/empty

```bash
echo "# empty" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:acacha/empty.git
git push -u origin main
```

## 103 Tercer vídeo. Pensar que volem fer -> Primer test

Link: https://youtu.be/6SxjClAdXZ8

Pensar els noms dels testos. Definim primer els noms i després el codi:
- Els usuaris poden veure vídeos -> users_can_view_videos
- Els usuaris poden veure vídeos publicats -> users_can_view_published_videos
- Els usuaris NO poden veure vídeos NO PUBLICATS -> users_cannot_view_unpublished_videos

Els Noms de testos que es puguin llegir en llenguatge natural i siguin una descripció del que comprova el test.

Altres:
- RIGHT PASS: pas correcte i pas incorrecte
- Valet: executar la nostra aplicació amb valet link i valet links

Coses que heu de saber/aprendre?
- Codis d'estatus i protocol HTTP -> 404 i 200, GET requests . Vegeu https://tubeme.acacha.org/HTTP
- URI i URLS. Vegeu https://tubeme.acacha.org/URL
- PHP artisan: Artisan console -> Laravel executat per línia de comandes: https://laravel.com/docs/8.x/artisan

Qüestions pendents:
- Tipus de Testos: Testos unitaris i testos de Feature
- [PHPUnit](https://phpunit.de/): és la llibreria que utilitzem per a fer testos amb PHP. Existeixen altres eines com PEST

Transcripció de comandes:

Crear i executar testos

```
$ php artisan make:test Videos/VideoTest
$ git status
$ phpunit
$ php artisan test

Executar un sol test

```
$ php artisan test test/Features/Videos/VideoTest
```

Parts de un test:

1) Preparació del codi que volem executar: preparar la base de dades, simular unes condicions prèvies, etc
2) Execució
3) Comprovació/assertions

IMPORTANT: Cal tenir en compte que els testos han de començar sempre des de un estat preconegut o estat zero. En el cas de Laravel sobretot cal tenir en compte que la base de dades estarà buida. 

Documentació Laravel sobre testos:
- https://laravel.com/docs/8.x/testing
- Testos HTTP: https://laravel.com/docs/8.x/http-tests

Conceptes vists als vídeos:
- Wishful programming: Escriure primer el codi que volem tenir i després fer que funcioni i no pas al revés. Està molt relacionat amb pensar sempre en la API de la nostra aplicació, és a dir primer centrar-nos en el que volem fer i després en el com
- API: Application Public Interface: part vísible (pública) del nostres codi, defineix la forma en que s'ha d'utilitzar el codi i per tant la interfície d'interacció entre el programador (usuari de la API/codi) i el codi. La API sól tenir tres parts:
  - Nom del mètode/funció/codi que volem utilitzar: obligatori
  - INPUT: paràmetres d'entrada: poden ser opcionals
  - OUTPUT: sortida, pot ser opcional (NULL) o pot ser un tipus bàsic de dades o qualsevol estructura de dades complexa de programació (arrays, llistes, objectes)

Enllaç al codi del primer test:

https://github.com/acacha/casteaching/blob/cfab8322d8fad4a70a104935abf3330c403690e9/tests/Feature/Videos/VideoTest.php

```php 
    public function users_can_view_videos()
    {
        // FASE 1 -> Preparació -> Prepare
        // WISHFUL PROGRAMMING -> API
        $video = Video::create([
                'title' => 'Ubuntu 101',
                'description' => '# Here description',
                'url' => 'https://youtu.be/w8j07_DBl_I',
                'published_at' => Carbon::parse('December 13, 2020 8:00pm'),
                'completed' => false,
                'previous' => null,
                'next' => null,
                'series_id' => 1
        ]);


        // FASE 2 -> Execució -> Executa el codi a provar
        // Laravel HTTP TESTS ->
        $response = $this->get('/videos/' . $video->id);


        // FASE 3 -> Assertions -> comprovacions
        $response->assertStatus(200);
        $response->assertSee('Ubuntu 101');
        $response->assertSee('Here description');
        $response->assertSee('December 13');
    }
```

Codi/commit:
- https://github.com/acacha/casteaching/tree/cfab8322d8fad4a70a104935abf3330c403690e9

# 104 Primer test en Verd

Errors més típics:
- TODO

# 105 Afegir Laravel Jetstream a la nostra aplicació

Coneixements previs:

[Laravel Jetstream](https://github.com/acacha/wiki/blob/main/LARAVEL_JETSTREAM.md): https://youtu.be/zyABmm6Dw64

# 106 Entorn de Testing i entorn Local, bases de dades diferenciades, migrate fresh seed

En aquest vídeo veiem la importància de tenir entorns (environments controlats pel fitxer .env)

Vídeo

Objectius:
- Saber com canviar les variables d'entorn a PHPUnit utilitzant el fitxer phpunit.xml
- Tenir clar que els testos parteixen d'un estat conegut inicial en cada test. Per tant en els testos de base de dades (trait RefreshDatabase) cada cop que executem un test la base de dades es buida i es torna a crear
- Cal tenir l'entorn local i l'entorn d'explotació separats, especialment pel que fa a base de dades. NO poden utilitzar la mateixa base de dades.
- Com es pot tenir en l'entorn local un estat preconegut de la base de dades útil per fer proves amb usuaris pre-generats, vídeos de proves .etc. Ús de seeders a Laravel.


# 107 Testos unitaris solució exercicis proposats, helpers i refactoritzacions

https://youtu.be/_rE2UE5J8Lk

Un test unitari a diferència d'un test de Feature prova de forma aillada una funció, un mètode o una clase. En canvi els test de Feature proven una "feature" o característica de l'aplicació i solen tenir en compte/provar varies coses al mateix temps

# 108 Laravel Blade components i Layouts

En aquest capitol comencem a refactoritzar les nostres vistes per millorar el "Look&Feel", la interfície gràfica (UI) però també la UX (User Experience) de la nostra aplicació

- Sistema de plantilles Laravel Blade: https://laravel.com/docs/8.x/blade
- Components: concepte força genèric també veurem a Vue i en frameworks CSS com Vuetify, Ionic. S'utilitzen elements HTML creat per nosaltres mateixos
- Els components laravel tenen un prefix per determinar un espai de noms segur i evitar col·lision de noms -> <x-NOM_COMPONENT_LARAVEL></x-NOM_COMPONENT_LARAVEL>
- Layouts: permeten compartir una shell o closca entre diferents pàgines d'una mateixa aplicació web

https://youtu.be/ofSbYUEml4c

# 109 Tailwind CSS i primer disseny vista show de vídeos

# TODO . Crear apartat Laravel Seguretat

Crear un vídeo de Laravel Breeze

Diferències entre:
- Laralve Breeze
- Laravel Jetstream
- Laravel Fortify
- Laravel Sanctum

Moure aquest apartat

Conceptes:

Laravel té un apartat dedicat a la seguretat:
- Middleware: https://laravel.com/docs/8.x/middleware . Middleware provide a convenient mechanism for inspecting and filtering HTTP requests entering your application. For example, Laravel includes a middleware that verifies the user of your application is authenticated. If the user is not authenticated, the middleware will redirect the user to your application's login screen. However, if the user is authenticated, the middleware will allow the request to proceed further into the application.
- Middleware com una forma de mantenir els controladors THIN (lleugers) i evitar Controladors FAT. També és una forma de centralitzar codi de controls d'accés i evitar codi WET

Laravel té una secció de seguretat amb els següents apartats
- Authentication: podeu crear el vostre propi sistema però es recomanable utilitzar un starter kit o adaptar-lo a les vostres necessitats.
  - No confondre l'autenticació amb l'autorització
  - Configuració config/auth.php
- Authorization
- Email Verification
- Encryption
- Hashing
- Password Reset


# 110 Seguretat. Control d'accés a recursos segons l'usuari. Autenticació

Vídeo previ sobre seguretat en Laravel

Tipus de seguretat:
- Control de visibilitat: estat dels vídeos published o unpublished

# Coneixements previs

- Sistema operatiu Ubuntu 20.04 preparat amb totes les eines necessaries per desenvolupar en Laravel. Veieu 
s://tubeme.acacha.org/101
- Entorn de desenvolupament amb Ubuntu Desktop: https://www.youtube.com/watch?v=w8j07_DBl_I
- Git i Github: https://www.youtube.com/watch?v=hRcIuEtXaBc
- GH: https://cli.github.com/
- Laravel valet | https://tubeme.acacha.org/laravel_valet

# Screencasts

Veieu els vídeos de com construir una aplicació Youtube/Screencasting per mostrar vídeos per Internet

[casteaching](casteaching.md)

# Codi font

https://github.com/acacha/casteaching

# TODO / Brainstorming

Github:
- Social login | [Laravel Socialite](https://laravel.com/docs/8.x/socialite) -> acceptar només Github per a fer login
- Desactivar Registre -> Només acceptar usuaris github? Si es poden soportar les dos coses millor. User profile poder vincular compte de Github

Connexió amb Github sponsors. Proves API

# Recursos
- https://course.testdrivenlaravel.com/
- [TDD](TDD.md)
- https://www.youtube.com/watch?v=hRcIuEtXaBc
- https://laravel.com/docs/8.x/http-tests#making-requests
