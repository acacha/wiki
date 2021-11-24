# LARAVEL SEGURETAT

Screencasts: https://tubeme.acacha.org/laravel_seguretat | https://tubeme.acacha.org/laravel_security

# Llista de vídeos:

Conceptes previs:
- HTTP: https://tubeme.acacha.org/http
- URL: https://tubeme.acacha.org/url
Laravel Starter Kits (https://laravel.com/docs/8.x/starter-kits)
- https://tubeme.acacha.org/laravel_breeze
- https://tubeme.acacha.org/laravel_jetstream

Autenticicació i autorització amb Laravel:
- https://tubeme.acacha.org/laravel_middleware
- https://tubeme.acacha.org/laravel_authentication
- https://tubeme.acacha.org/laravel_authorization | TODO
- https://tubeme.acacha.org/laravel_fortify

Token authentication:
- https://tubeme.acacha.org/laravel_token | TODO
- https://tubeme.acacha.org/laravel_sanctum | TODO
- https://tubeme.acacha.org/laravel_passport | TODO
- https://tubeme.acacha.org/laravel_sociallogin  | TODO

Veieu també els videos del curs https://tubeme.acacha.org/tdd:
- 113. Exemple d'autorització amb TDD: https://www.youtube.com/watch?v=jX6aHnvWOO4&list=PLyasg1A0hpk0Irrc0YE_OVY-8A2rUnJZU&index=8

# NOTES

- [ ] Laravel Middlewares by example -> Authentication
- [ ] Crear un vídeo de Laravel Breeze
- [X] Crear un video de Laravel Jetstream

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
