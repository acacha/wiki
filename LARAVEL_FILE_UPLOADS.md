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

# Recursos
- https://laravel.com/docs/8.x/filesystem
- https://github.com/thephpleague/flysystem
