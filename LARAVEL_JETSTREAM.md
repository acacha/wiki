# SCREENCAST

https://tubeme.acacha.org/laraveljetstream

# Codi font

https://github.com/acacha/laravel_jetstream

# Coneixements previs

- [Composer](): Saber instal·lar paquets PHP amb composer
- [Laravel](https://github.com/acacha/wiki/blob/main/Laravel.md): Coneixements bàsics de Laravel
  - [Laravel Artisan](): saber executar comandes Laravel
  - [Laravel Packages](): Breeze és un paquet PHP però sobretot és un paquet Laravel. És a dir, com tot paquet Laravel és condició necessaria ser un paquet PHP i per tant utilitza Composer, però a més és un paquet PHP que no té sentit utilitzar fora de Laravel pq està pensat per ser utilitzat amb laravel.
- [Livewire](): NO cal ser un expert per començar però almenys saber què és pot ajudar.
- [NPM]() i [Laravel Mix](): Cal conèixer lo bàsic, és a dir que Laravel utilitza una eina que és diu Laravel Mix, que realment és un webpack adaptat per a Laravel que utilitza script npm per gestionar els assets Javascript de la nostra aplicació Laravel. Full Stack development
- [Laravel Bases de dades](): Migracions i configuració bàsica de base de dades. Comanda php artisan migrate.
- [Laravel valet](): Per provar l'aplicació.
# Què és?

Segons la documentació (https://laravel.com/docs/8.x/starter-kits) es tracta d'un dels starter kits de Laravel. Proporciona un scaffolding/una plantilla bàsica amb funcionalitat habitual com Authenticació, Login i Registre i altres.

# Passos

```bash
laravel new casteaching_teacher && cd casteaching_teacher
composer require laravel/jetstream
php artisan jetstream:install livewire --teams
npm install
npm run dev
```

Configuració de la base de dades. De moment us recomano utilitzar una base dades sqlite que ja migrarem a base de dades SQL. Editeu fitxer .env.

Canvieu

```diff
- DB_CONNECTION=mysql
- DB_HOST=127.0.0.1
- DB_PORT=3306
- DB_DATABASE=casteaching
- DB_USERNAME=root
- DB_PASSWORD=
+ DB_CONNECTION=sqlite
+ #DB_HOST=127.0.0.1
+ #DB_PORT=3306
+ #DB_DATABASE=casteaching_teacher
+ #DB_USERNAME=root
+ #DB_PASSWORD=

```

I executeu:

```bash
touch database/database.sqlite
apt-get install php7.4-sqlite
php artisan migrate
```

Suposem teniu [Laravel Valet]() instal·lat:

```bash
valet link
valet open
```
I

# Screencast

IMPORTANT -> treure driver sqlite per veure els errors

# Recursos
- https://laravel.com/docs/8.x/starter-kits
- https://jetstream.laravel.com/2.x/introduction.html
