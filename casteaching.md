# Temes currículars que tractarem

- MP9 UF1: Seguretat. Accés a recursos publicats o no publicats, usuaris registrats i no registrats, autoritzacions (subscriptors)
- MP7 UF2: TDD, testos manuals i testos automàtics

# Notes vídeos

## Primer vídeo. Introducció

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

## Segon vídeo. Creació del projecte Laravel i repositori Github

NOTES: S¡acaba bruscament i alguna edició extra que caldria afegir.

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

## Tercer vídeo. Pensar que volem fer -> Primer test
- Pensar els noms dels testos. Definim primer els noms i després el codi
- Noms de testos que es puguin llegir en llenguatge natural i siguin una descripció del que comprova el test
- RIGHT PASS: pas correcte i pas incorrecte
- Valet: executar la nostra aplicació amb valet link i valet links

Coses que heu de saber/aprendre?
- Codis d'estatus i protocol HTTP -> 404 i 200, GET requests . Vegeu https://tubeme.acacha.org/HTTP
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

Enllaç al codi del primer test:

- 

# Coneixements previs

- Sistema operatiu Ubuntu 20.04 preparat amb totes les eines necessaries per desenvolupar en Laravel. Veieu https://tubeme.acacha.org/101
- Entorn de desenvolupament amb Ubuntu Desktop: https://www.youtube.com/watch?v=w8j07_DBl_I
- Git i Github: https://www.youtube.com/watch?v=hRcIuEtXaBc
- GH: https://cli.github.com/
- Laravel valet | https://tubeme.acacha.org/laravel_valet

# Screencasts

Veieu els vídeos de com construir una aplicació Youtube/Screencasting per mostrar vídeos per Internet

[casteaching](casteaching.md)

# Codi font

https://github.com/acacha/casteaching

# Recursos
- https://course.testdrivenlaravel.com/
- [TDD](TDD.md)
- https://www.youtube.com/watch?v=hRcIuEtXaBc
- https://laravel.com/docs/8.x/http-tests#making-requests
