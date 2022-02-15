# Screencast

- [136 Refactorització vistes amb Laravel Blade i Jetstream Components. Preparació File uploads i CRUD de series](https://youtu.be/ZTPgnELm3Lg)
- [137 TDD File Uploads](https://youtu.be/f_Yjaj-gekw)
- [138 Refactorització codi existent i Validació d'imatges](https://youtu.be/P-VbDKUrQ0M)

De la sèrie [TDD Laravel d'acacha_dev](https://tubeme.acacha.org/tdd)

![image](https://user-images.githubusercontent.com/4015406/153370856-4aed0c84-a69a-4650-af02-89822a4ab371.png)

Pròxim contingut:
- [Processament d'imatges. Multimedia imatges i vídeo](https://github.com/acacha/wiki/blob/main/MULTIMEDIA_IMATGES_i_VIDEOS.md)

# Guió

- Us proporciono el CRUD de series ja que es tracta d'un copia/pega del CRUD de videos que no aporta res que no haguim vist fins ara. Branca [crud_series](https://github.com/acacha/casteaching/tree/crud_series). La branca ja està incorporada a main.
- Exemple de com fer un merge amb branques remotes: [git remote add acacha git@github.com:acacha/casteaching.git | git fetch acacha crud_series
 | git checkout main | git merge acacha/crud_series](https://stackoverflow.com/questions/21651185/git-merge-a-remote-branch-locally)
- Comproveu els tests i que teniu una nova secció Series a l'aplicació
- Afegir secció per modificar(update/PUT) la imatge d'una serie.
- Inputs de fitxers a HTML: [input type file](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/file)
- Gestió de fitxers amb Laravel. Concepte de driver. Avantatges e invonvenients de cada driver

Formulari edició/update imatge de la serie. Comparació amb https://casteaching.test/user/profile
- Evitar codi wet també amb HTML. Com? utilitzant components UI reutilitzables. Similar al que ja fem amb Ionic però en comptes de components ja existents proporcionats per un framework utilitzar els nostres propis o els que es proporciona Laravel (en aquest cas la plantilla Laravel JetStream)
- Dos tipus de components: Laravel Blade Components (prefix x: <x-component-name>) o compoents LiveWire (veurem més endavant).
- Exercici: refactorització de les plantilles blade de vides/users/series per tar d'utilitzar components i reduir codi WET i fer codi DRY HTML

TDD (Test Driven Development):
- Comprovar que tenim una nova secció a edit:  
- TDD del procesament del formulari:
- Nou controlador i nou test utilitzant TDD i tècniques testing Laravel file uploads
- ON he après estas tècniques?: https://course.testdrivenlaravel.com | https://course.testdrivenlaravel.com/lessons/module-27/faking-uploads-and-file-systems#139 - Codi Adam wathan TDD: https://github.com/nothingworksinc/ticketbeast/commit/7cded06a0b2d2bcf5c8f32567a2b22ece1105fe2

 Vídeo 138:
 - Canvis a seeders per utilitzar correctament les imatges i canvis al youtube import.
 - Comprovar no només que el fitxer existeix sinó a més que és el mateix [Codi](https://github.com/nothingworksinc/ticketbeast/commit/b95e75dd6bbd627db6c4432cc4fdfda9150b33f0)
 - [Validació](https://github.com/nothingworksinc/ticketbeast/commit/e18ba35efdc75241ed3622828cc772d45adb3785):
 
Relació d'aspecte:
- Miniaturas de Youtube un 16:9 [Link](https://www.google.com/search?q=miniatura+youtube+tama%C3%B1o&oq=miniatura+youtube&aqs=chrome.1.69i57j0i512l9.8345j0j7&sourceid=chrome&ie=UTF-8)
- Los tipos de archivos aceptados son JPG, GIF o PNG, que no superen los 2 MB.
- Disseny original: https://tailwindui.com/components/marketing/sections/blog-sections#component-720cf60b960fecb99c45f462f24db2d9
 
# Gestió de fitxers

Filesystem abstraction/API: una forma comuna de treballar amb fitxers amb independència del driver (sistema a utilitzar: local(Linux/Windows/Mac), al núvol, etc). 

NO cal canviar el codi (api comuna) si es canvia de driver.

- https://laravel.com/docs/8.x/filesystem

# Paths

Helpers per ajudar amb els paths

- https://laravel.com/docs/8.x/helpers#paths-method-list

# Manipular File contents

## En cru

Mètodes PUT i GET
- Storage::disk('local')->put('example.txt', 'Contents');

FileStreamers -> OHH NOOO! es tant baix nivell, quin pal!

## Laravel automatic file streaming

https://laravel.com/docs/8.x/filesystem#automatic-streaming

## Manipulació fitxers CS

Laravel Excel: https://laravel-excel.com/

Exemple Importació Usuaris:
- https://docs.laravel-excel.com/3.1/imports/

TODO
Casteaching: 
- Vídeo comanda que permeti importar usuaris d'un fitxer CSV
- Exercici: ídem per a vídeos, fer interfície Upload and process file

Instal·lació:
- https://docs.laravel-excel.com/3.1/getting-started/installation.html

# File Uploads

https://laravel.com/docs/8.x/filesystem#file-uploads

## Testing

Tenim una classe **UploadedFile** que permet crear fitxers de mentira per testejar File Uploads i permet indicar les característiques del fitxer:

``` 
UploadedFile::fake()->image('photo1.jpg')
```

- https://laravel.com/docs/8.x/http-tests#testing-file-uploads
- https://laravel.com/docs/8.x/mocking#storage-fake

# Testing (TDD)

Quan es fan testos relacionats amb fitxers NO voldrem mai acabar modificant el sistema de fitxers real de la nostra aplicació, ni el local, ni el de producció.

Per això s'utilitza un Fake, veieu Storage fake:

- https://laravel.com/docs/8.x/mocking#storage-fake

# Prova amb Amazon S3

- Fer un pas a pas com obtenir token amb alumnedam@iesebre.com

https://dev.to/aschmelyun/getting-started-with-amazon-s3-storage-in-laravel-5b6d

Alternatives a Amazon S3:
- https://laravel.com/docs/8.x/filesystem#amazon-s3-compatible-filesystems

# Image manipulation

```
composer require intervention/image
```

Recursos:
- https://image.intervention.io/v2

# TDD. Adam wathan curs

Primer un happy path
HAPPY PATH
- Faking Uploads and File Systems: Fakes de Laravel per provar fitxers sense tocar storage real. Incorpora assercions per comprovar existeixen fitxers
- Comparing content -> Com a més que existeixi es pot comparar contingut.
ERRORS I VALIDACIONS 
- Validació: es determina una mida mínima (ample) per a les imatges i un aspect ratio
Optimització:
- Processament de les imatges. Llibreria intervention. Utilització de Jobs per optimitzar la imatge. Spatie media library: https://spatie.be/docs/laravel-medialibrary/v9/introduction

Recursos:
- https://course.testdrivenlaravel.com/lessons/module-27/faking-uploads-and-file-systems#139

# Recursos
- https://laravel.com/docs/8.x/filesystem
- https://github.com/thephpleague/flysystem
- https://course.testdrivenlaravel.com/lessons/module-27/faking-uploads-and-file-systems#139
