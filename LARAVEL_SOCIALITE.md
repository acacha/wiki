# Screencasts

- [134 2022 01 28 Laravel Socialite | Github Login | Exemple de creació testos a posteriori i mocks](https://youtu.be/OUtoSt-vmCo): Laravel Socialite - Login amb Github i exemple de com crear testos a posteriori de la escriptura de codi. Mocking Facades

De la sèrie TDD Amb Laravel: https://tubeme.acacha.org/tdd

![Blue Geeky Laptop Apology Card](https://user-images.githubusercontent.com/4015406/151547787-c4d8324a-3a22-4548-8b56-7932381950b0.png)


# Guió

Exemple d'afegir testos a un codi ja existent. És a dir, no fem TDD (Test Driven Development), ja que primer fem el codi i després el test.

També es segueix aquest flux quan es vol Refactortizar codi existent de forma segura o simplement per que volem afegir tests a la nostra aplicació.

Exemple amb Casteaching:
- Branca Github: https://github.com/acacha/casteaching/tree/github
- Instal·lació composer require
- Configuració services.php
- Obtenció de GITHUB_CLIENT_ID | GITHUB_CLIENT_SECRET
- URL: https://docs.github.com/en/developers/apps/building-oauth-apps/creating-an-oauth-app

Refactorització
Branca de refactorització:

Codi exemple:

https://github.com/acacha/casteaching/blob/github/routes/web.php#L62-L105

# Testos a posteriori

Refactorització
- Tenim un codi ja existent i volem poder canviar-lo amb seguretat
- Creem un controlador: GithubAuthController i el seu test GithubAuthControllerTest
- Wishful programming (definem la API que voldriem) i codi més expresiu

Testos a realitzar

- redirects_to_github
- can_process_a_callback

# Estrategies

- Només Login amb Github -> Inconvenient: molt limitat a només desenvolupadors i fins i tot pot haver algunes persones no vulguin utilitzar
- Correu electrònic: sempre és la base de marketing, important aconseguir contactes/emails
- Les dos coses suposen afegir camps a la taula users i fer una gestió de totes les posibilitats

# TODO

Al perfil poder canviar la vinculació amb Github d'un usuari.

# Recursos
- https://laravel.com/docs/8.x/socialite
