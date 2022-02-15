# Screencasts

- [140 Optimització d'imatges utilitzant Events i Jobs de Laravel amb TDD](TODO URL)

De la sèrie [TDD Laravel d'acacha_dev](https://tubeme.acacha.org/tdd)

![image](https://user-images.githubusercontent.com/4015406/153370856-4aed0c84-a69a-4650-af02-89822a4ab371.png)

# Continguts Previs

- [Laravel File Uploads](https://github.com/acacha/wiki/blob/main/LARAVEL_FILE_UPLOADS.md)
- [Upgrade a Laravel 9](https://github.com/acacha/wiki/blob/main/LARAVEL_9.md)

# Imatges, file uploads i Laravel. Presentació

Com passar d'una UI:

![image](https://user-images.githubusercontent.com/4015406/153841300-7c8f6d55-ea17-4073-9730-6cfef05283df.png)

A:

![image](https://user-images.githubusercontent.com/4015406/154020586-045ebd31-56d2-4ee6-b010-5369677e9c13.png)

Qüestions a tenir en compte:
- Quan les imatges poden ser nullables (per tant la imatge és opcional). Quina imatge mostrar quan no hi ha imatge?
- Múltiple solucions: (UI Avatars)[https://eu.ui-avatars.com/] utilitza les inicials del nom usuari
- Gravatar: utilitzar la imatge de Gravatar(WordPress)
- https://www.producthunt.com/alternatives/ui-faces | https://github.com/topics/avatars
- Github: Identicons: https://github.blog/2013-08-14-identicons/
- https://barro.github.io/2018/02/avatars-identicons-and-hash-visualization/
- https://github.com/download13/blockies

# Guió (Optimització imatges)

- Primer pas: Testing Events. Disparar un esdeveniment cada cop s'actualitza/afegeix una imatges. [Laravel mocks. Event fake](https://laravel.com/docs/9.x/mocking#event-fake)
- Nom Event: SeriesImageUpdated.php . Injecció de dependències: $serie
- TDD: FAking events i asserting:  [Laravel mocks. Event fake](https://laravel.com/docs/9.x/mocking#event-fake)
- Segon pas: Testing Event Listener
- Configuració del event Listener: Creació del EventListener: ScheduleSeriesImageProcessing.php i configuració a EventserviceProvider
- Nom del test: it_queues_a_job_to_process_a_poster_image_if_a_poster_image_is_present
- Comprovació que si es dispara un event es processa un Job -> Queue::fake() | Queue::assertPushed()
- Tercer Pas: Realment es testeja un Job: ProcessSeriesImage.php
- Carpeta Unit/Listeners per fer testos unitaris (utilitzant però el TestCase de Laravel no el de PHPUnit) per provar el ProcessSeriesImage (ProcessSeriesImageTest.php)
- TDD: Escriptura del Test
- Codi final de processament de la imatge

# Guió Passos previs (behind the scenes)

Primer us mostro els canvis realitzats a la branca [millores_ui_fileuploads](https://github.com/acacha/casteaching/tree/millores_ui_fileuploads) branca que juntarem (merge) amb main.

Mostrar una imatge per defecte quan no hi ha imatge associada a la serie com:

![Blue Elegant Minimalist Gadget Review YouTube Thumbnail](https://user-images.githubusercontent.com/4015406/153844292-743d51e5-3534-49fe-9c38-4f328512b3b7.png)

En comptes de:

![image](https://user-images.githubusercontent.com/4015406/153844532-680f1138-5107-455b-b68f-1340ee84db09.png)

I el mateix amb el teacher. Utilitzem un avatar per defecte per als usuaris anònims:

https://avatars.dicebear.com/api/identicon/:seed.svg

Exemple:

![image](https://user-images.githubusercontent.com/4015406/154021315-9ea941f8-51ea-4120-90b7-c583f6e91e26.png)

Tècniques i codi utilitzat:
- Nou sistema d'[accessors amb Laravel 9](https://laravel.com/docs/9.x/eloquent-mutators#defining-an-accessor) per tal de proveir un camp calculat que depèn del camp image. Si image no és null s'utilitza el camp image directament i sinó un valor per defecte.
- TDD de Series(SeriesTest) per comprovar el funcionament de l'accessor
- Ús en plantilles blade de ?? | https://www.php.net/manual/en/migration70.new-features.php | Null Coalescing operator | Alternativa a isset()

# Optimització imatges

## Intervention Image

[Gist](https://gist.github.com/acacha/bfde561838766cf2a23d888e5b0840d2.js)

```php
$imageContents = Storage::disk('public')->get($this->concert->poster_image_path);
$image = Image::make($imageContents);
$image->resize(600)->encode();
Storage::disk('public')->put($this->concert->poster_image_path, (string) $image);
```

Recursos:
- https://intervention.io/

# Recursos
- [Curs TDD Adam Wathan i optimització Imatges amb  ](https://course.testdrivenlaravel.com/lessons/module-28/testing-events#143)

# blur hashing images

https://blur-hash.com/#/

# Recursos
- [Curs TDD Adam Wathan i optimització Imatges amb  ](https://course.testdrivenlaravel.com/lessons/module-28/testing-events#143)
