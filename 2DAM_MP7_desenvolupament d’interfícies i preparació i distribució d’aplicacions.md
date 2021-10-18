# UF2 Preparació i distribució d’aplicacions


https://user-images.githubusercontent.com/4015406/137270070-c8239c9c-fce1-4929-a145-f8ed4d43138f.mp4


## Introducció

Aquesta unitat formativa tot i ser la segona la realitzem la primera abans de la d'interfícies ja que així podrem des de un bon principi treballar per projectes i a més que aquests projectes siguin projectes els menys "juguet" possible. És a dir, primer us ensenyem a preparar i distribuir les aplicacions i durant la resta del curs fem ús d'aquests coneixements de forma transversal i continuada. Aquí apliquem el **RA3** (Prepara aplicacions per a la seva distribució avaluant i analitzant eines específiques.)

Cal tenir en compte a més que en aquesta UF s'estableixen les bases per a (Primer i Segon criteri d'avaluació):
- **RA1** Avaluar el funcionament d’aplicacions dissenyant i executant proves. Expliquem que són les proves i durant el curs les apliquem ja sigui manualment o amb TDD (Test Driven Development)
- **RA2** Documenta aplicacions seleccionant i utilitzant eines específiques. Des de un bon principi fem ús d'eines com Gihub (el codi font és la milor documentació) i els formwats Wiki com Markdown per tal de documentar.

# YOUTUBE

Screencasts, elstrobareu a la playlist:
- https://www.youtube.com/playlist?list=PLyasg1A0hpk2MhbwKbDimNHQXmdqC8CYi

Ordre dels vídeos: 
- [2021 10 06 19 32 19 101 COMPOSER](https://youtu.be/XBKg-EYW0nM)
- [2021 10 06 16 30 16 NODEJS NPM 101](https://youtu.be/tdVbtP4xtk0)
- [2021 10 13 17 03 32 JavascriptBundlesBuildtoolsLaravelMixwebPackViteiVue](https://youtu.be/VmlSy0Y7uso)


# Materials

## Distribució d’aplicacions

- **Situació en el currículum**: Apliquem el **RA3** Prepara aplicacions per a la seva distribució avaluant i analitzant eines específiques i els seus corresponents CA i continguts

Els següents materials seran continguts transversals per a tot el curs que es permetren distribuir totes les aplicacions que desenvolupem durant el curs segons l'entorn i o llenguatge de programació

### Backend, entorns de servidor

Bàsicament utilitzarem dos llenguatges de programació

**Javascript**:
- [NodeJS i distribució aplicacions Javascript. Mòduls ES6](https://github.com/acacha/wiki/blob/main/NODE_JS.md): En aquesta article trobareu informació sobre NodeJs i Javascript i el gestor de paquets NPM. També trobareu continguts sobre programació modular amb Javascript (Mòduls ES6 i historia versions Javascript i mòduls). També us ensenyo a distribuir aplicacions Javascript amb NPM.


**PHP**
- [COMPOSER i PHP](COMPOSER_PHP.md): La importància de composer en el món de PHP com a gestor de paquets, veiem també el repositori packagist i exemples d'ús a Laravel. 

Un cop dominats els llenguatges de backend del curs veiem:
- Distribució aplicacions backend dinàmiques: Amb Digital Ocean i Laravel Forge. Aprendreu a crear el vostre propi servidor
- Distribució aplicacions backend estàtiques: en aquest cas el servidor funciona com un simple contenidor de fitxers i realment l'execució dinàmica de codi es fa al frontend. Consulteu l'apartat de frontend

### Frontend, entorns de client

Bàsicament utilitzarem dos llenguatges de programació o entorns
- **Javascript i lleguatges de marques**: S'utilitza el mateix sistema -> NPM de NodeJS i per tant els continguts apresos a entorns de backend també serveixen.
- **Android**: Utilitzem Kotlin com a llenguatge de programació. La distribució d'aplicacions Android la fem al [MP8](https://github.com/acacha/wiki/blob/main/2DAM_MP8_Programaci%C3%B3%20multim%C3%A8dia%20i%20dispositius%20m%C3%B2bils.md)


# Currículum

## Continguts

1. Realització de proves:
- 1.1 Objectiu, importància i limitacions del procés de prova. Estratègies.
- 1.2 Proves d’integració: ascendents i descendents.
- 1.3 Proves de sistema: configuració, recuperació, entre d’altres.
- 1.4 Proves d’ús de recursos.
- 1.5 Proves de seguretat.
- 1.6 Proves manuals i automàtiques. Eines de programari per a la realització de proves.

2. Documentació d’aplicacions:
- 2.1 Fitxers d’ajuda. Formats.
- 2.2 Eines de generació d’ajudes.
- 2.3 Taules de continguts, índexs, sistemes de cerca, entre d’altres.
- 2.4 Tipus de manuals: manual d’usuari, guia de referència, guies ràpides, manuals d’instal·lació, configuració i administració. Destinataris i estructura.

3. Distribució d’aplicacions:
- 3.1 Components d’una aplicació. Empaquetatge.
- 3.2 Instal·ladors.
- 3.3 Paquets autoinstal·lables.
- 3.4 Eines per crear paquets d’instal·lació.
- 3.5 Personalització de la instal·lació: logotips, fons, diàlegs, botons, idioma, entre d’altres.
- 3.6 Assistents d’instal·lació i desinstal·lació.

## Resultats d’aprenentatge i criteris d’avaluació

1. Avalua el funcionament d’aplicacions dissenyant i executant proves.

Criteris d’avaluació

- 1.1 Estableix una estratègia de proves.
- 1.2 Realitza proves d’integració dels diferents elements.
- 1.3 Realitza proves de regressió.
- 1.4 Realitza proves de volum i d’estrès.
- 1.5 Realitza proves de seguretat.
- 1.6 Realitza proves d’ús de recursos per part de l’aplicació.
- 1.7 Documenta l’estratègia de proves i els resultats obtinguts.

2. Documenta aplicacions seleccionant i utilitzant eines específiques.

Criteris d’avaluació
- 2.1 Identifica sistemes de generació d’ajudes.
- 2.2 Genera ajudes als formats habituals.
- 2.3 Genera ajudes sensibles al context.
- 2.4 Documenta l’estructura de la informació persistent.
- 2.5 Confecciona el manual d’usuari i la guia de referència.
- 2.6 Confecciona els manuals d’instal·lació, configuració i administració.
- 2.7 Confecciona tutorials.

3. Prepara aplicacions per a la seva distribució avaluant i analitzant eines específiques.

Criteris d’avaluació

- 3.1 Empaqueta els components que requereix l’aplicació.
- 3.2 Personalitza l’assistent d’instal·lació.
- 3.3 Empaqueta l’aplicació per ser instal·lada de forma típica, completa o personalitzada.
- 3.4 Genera paquets d’instal·lació fent servir l’entorn de desenvolupament.
- 3.5 Genera paquets d’instal·lació fent servir eines externes.
- 3.6 Genera paquets instal·lables en mode desatès.
- 3.7 Prepara el paquet d’instal·lació perquè l’aplicació pugui ser correctament desinstal·lada.
- 3.8 Prepara l’aplicació per ser descarregada des d’un servidor web i executada.

# Recursos
- Curriculum: http://xtec.gencat.cat/web/.content/alfresco/d/d/workspace/SpacesStore/0052/64a26049-c0c0-45cc-baa0-a4f831059839/DOGC_TS_desenvolupament_aplicacions_multiplataforma.pdf
- Apunt IOC: 
