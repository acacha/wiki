Documentació per a https://github.com/Desenv-Aplicacions-Multiplataforma/2DAM_2021_22#phaser

http://richard.to/programming/too-many-cooks-part-1.html

# Exemples assets

- https://bayat.itch.io/platform-game-assets | http://richard.to/programming/too-many-cooks-part-1.html
- https://opengameart.org/ | https://opengameart.org/collections | Podeu ordenar per favorits
- [Kenney](https://kenney.nl/) | https://opengameart.org/content/kenney-16x16 | https://opengameart.org/content/platformer-art-pixel-redux | https://mozdevs.github.io/html5-games-workshop/en/guides/platformer/start-here/ | https://gamedevacademy.org/how-to-make-a-mario-style-platformer-with-phaser-3/
- Super Mario: https://github.com/acacha/mario | https://github.com/acacha/mario/tree/master/assets/tilemaps/tiles | https://www.webtips.dev/webtips/phaser/remake-mario-in-phaserjs-part1
- Música: https://opengameart.org/content/happy-adventure-loop | The background music track, Happy Adventure, has been created by Rick Hoppmann.
- Summer:  https://github.com/marcmartimas17/PhaserGame/blob/master/assets/summer_tileset.png | https://github.com/marcmartimas17/PhaserGame | https://free-game-assets.itch.io/rpg-summer-tileset | 
- Platform pack tilesheet | https://github.com/j-aidle/j-aidle.github.io/blob/master/assets/tilesets/platformPack_tilesheet.png | https://stackabuse.com/phaser-3-and-tiled-building-a-platformer/ | https://github.com/StackAbuse/creating-a-platformer-with-phaser-3
- https://github.com/maksymkhar/PhaserPlatformGame/blob/master/assets/map/tilesheet.png

# Jocs alumnes altres anys
- https://github.com/deltcod/Phaser-Platform-Game | https://deltcod.github.io/Phaser-Platform-Game
- https://github.com/Germangalia/Phaser-Platform-Game | https://Germangalia.github.io/Phaser-Platform-Game
- https://maksymkhar.github.io/PhaserPlatformGame/ | https://github.com/maksymkhar/PhaserPlatformGame
- https://marcmartimas17.github.io/PhaserGame/ | https://github.com/marcmartimas17/PhaserGame
- https://j-aidle.github.io/ | https://github.com/j-aidle/j-aidle.github.io 
- https://josepaltadill.github.io/iceGame/ | https://github.com/josepaltadill/iceGame/
- https://byelyas.github.io/JocPhaser_Elies/ | https://github.com/ByElyas/JocPhaser_Elies
- https://davidm151.github.io/JocPhaser/ | https://github.com/davidm151/JocPhaser
- https://aycorreia.github.io/phaserjoc/ | https://github.com/aycorreia/phaserjoc

- http://acacha.org/mediawiki/2DAM_2016-17/Phaser.js
- Sergio Tur Badenas: http://comfortable-flock.surge.sh/
- http://tboy-manel.surge.sh/
- http://davidmgilo-platformer.surge.sh/
- http://rogermelich_platformgame.surge.sh/
- http://mr-rabbot-game.surge.sh/
- http://big-hearing.surge.sh/
- http://circus_game_es6.surge.sh/

# JOC PHASER A ENTREGAR (especificacions per al final)

Característiques del joc:

- Joc 2d fet amb Phaser
- Joc de plataformes
- Física arcade
- Ha de tenir mínim 3 scenes:
  - Escena inici del joc: presentació del joc i opcións mínimes: Jugar i Sortir. A aquest escena s'ha de tornar cada 
  cop l'usuari gasti les vides. Opcional: implementar un ranking o altres opciones menú inicia
  - Escena 1: Comenceu a densevolupar aquesta escenaAmb l'aplicació tiled, creeu un mapa fet amb tilesheets. Els assets a escollir són lliures. Us recomano mida
  mínima del tile: 64x64
  - Escena 2: igual que la 2 però s'arriba un cop superada la primera escena (arribar a una porta o quelcom similar indica final escena 1). Opcionalment podeu fet una còpia de
  la primera escena si us falta temps
  - Escenas en phaser: https://desarrolloweb.com/articulos/escenas-juegos-phaser
  - https://phaser.io/examples/v3/category/scenes
- Joc d'un jugador (no cal multijugador)
- Implementar un jugador que tingui animacions al moure's. Phaser animations/Spritesheets
- Control del moviment del jugador per teclat. Busqueu Input API. Opcional: Gamepad api
- El joc ha de tenir colleccionables, és a dir monedes, diamants etc. Aquest collecionables determinaran la puntuació. 
El joc a de tenir per tant un score que mostri la puntuació i les vides que li queden.
- Els collecionables han de tenir algún efecte al ser recollits (vegeu transformacions, exemple milkshake o similar).
- Implementar enemics. Poden estar quiets. És opcional posar algún tipus de moviment als enemics i/o IA
- Implementar zones que provoquen la mort: tipus el suelo és Lava o aigua.
- Implementar sistema de vides. L'usuari si colisiona amb un enemic (o opcionalment bales o similar) si encara te vides torna a començar la escena.
- Implementar mort del jugador:
  - Utilitzar algun efecte de camera tipus shake
  - Utilitzar un efecte de so al morir.
  - Si la mort és definitiva (s'acaben les )
  
OPCIONAL:
- Que el player o players puguin disparar objectes (bales o similars) i matin els enemics. Un altre opció es matar-los al saltar per sobre.
- Efecte/animació/font/explosió al matar un enemic.
- TODO
- Idees?  
  


# Presentació

https://jaumeramos.github.io/asteroids

# Passos a seguir

Bàsicament teniu un món de tutorials disponibles a:

https://phaser.io/learn

El guió que us proposo:

1) Seguir el tutorial Getting started (següent apartat)
2) Creeu el vostre primer joc seguint l'apartat el vostre primer joc (Make your fist game)
3) Feu l'exemple de spritesheets de més abaix
4) Publiqueu el codi a render i entregueu editant aquest fitxer via PR [vegeu apartats per entregar més abaix](https://github.com/Desenv-Aplicacions-Multiplataforma/2DAM_2021_22#phaser)

## Getting started

Feu el primer joc Hello World i llegiu tots els requeriments. Com experts en Javascript, npm/nodeJS, editors web a aquestes alçades ja no us vindrà res de nou.

https://phaser.io/tutorials/getting-started-phaser3

## Make your first game

IMPORTANT: Us donen un zip amb el codi de cada part -> No sigueu tristos, valtros utilitzeu Git ;-), creeu un repo, feu commits com a mínim a cada part i porteu la gestió de versions com pertoca en el món actual de programació.

Recursos:
- https://phaser.io/tutorials/making-your-first-phaser-3-game

# Texture Packer

```bash
wget https://www.codeandweb.com/download/texturepacker/6.0.1/TexturePacker-6.0.1.deb
sudo dpkg -i TexturePacker-6.0.1.deb
```

# Plantilla phaser 3

https://github.com/photonstorm/phaser3-project-template

Exemple:

```
git clone git@github.com:photonstorm/phaser3-project-template.git MyProject
cd MyProject
npm install
npm start
```

# SpriteSheets

Coneixements previs:
- Vegeu apartat anterior plantilla phaser 3
- Vegeu i instal·let Texture Packer

Seguiu el Tutorial:

https://www.codeandweb.com/texturepacker/tutorials/how-to-create-sprite-sheets-for-phaser3?utm_source=ad&utm_medium=banner&utm_campaign=phaser-2018-10-16

Demo project:
- https://github.com/CodeAndWeb/TexturePacker-Phaser3

# Documentació antiga

http://acacha.org/mediawiki/Phaser#.Yl6_YoRBxhE

# Recursos

https://github.com/acacha/wiki/new/main
