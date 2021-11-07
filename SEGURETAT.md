# Teòria 

Els continguts de la IOC tenen la teòria bàsica:
- https://ioc.xtec.cat/materials/FP/Recursos/fp_smx_m06_/web/fp_smx_m06_htmlindex/index.html
- https://ioc.xtec.cat/materials/FP/Recursos/fp_smx_m06_/web/fp_smx_m06_htmlindex/material_pdf.html

# Seguretat en Aplicacions i desenvolupament

Per a DAM (Desenvolupament aplicacions multiplataforma) trobo que el més adequat és aplicar els continguts teòrics a la pràctica en el desenvolupament aplicacions web

Exemples de projectes i aplicacions on utilitzem seguretat (com usuaris/desenvolupadors):

**Autenticació**:

Tot els casos que utilitzem són basats en el concepte de repte/resposta. Protocolos de reto/respuesta: https://es.wikipedia.org/wiki/Protocolos_desaf%C3%ADo-respuesta | https://en.wikipedia.org/wiki/Challenge%E2%80%93response_authentication
- Login: Github, Laravel Forge, Screencasts
- Autenticació en dos pasos: necessari per exemple en Github per tal de poder cobrar dels sponsors
- Autenticació entre aplicacions: Token -> Github CLI
- Autenticació basada en claus asimètriques: Github SSH
- Accés a servidor Digital Ocean utilitzant claus SSH

Però també crearem els nostres propis reptes/sistemes autenticació:
- Aquí és molt important no reiventar la roda. Si algún cas creeu un sistema autenticació a mida no el feu mai des de zero, utilitzeu llibreries.
- Vegeu apartat Laravel Autenticació

**Encriptació**
- SSH: protocol que substitueix FTP i Telnet per a la trasnferència i gestió remota de servidors
- HTTPS: Totes les web que farem tindran suport per a HTTPS
- En general totes les comunicacions de xarxa que farem a producció seran segures

## Desenvolupament d'aplicacions i seguretat

### Autenticació Backend

#### Laravel / Aplicació web

Objectiu:
- Afegir autenticació al projecte que estem realitzant
- Afegir autenticació en dos pasos
- Compliment llei: usuaris puguin eliminar les seva compte d'usuari

#### API. Token Based authentication

Objectiu:
- Afegir autenticació a la API REST del projecte que estem realitzant

### Videos

HTTPS:
- Activar HTTPS en local amb Laravel Valet, Instal·lació certificat
- Activar HTTPS amb LetsEncript i Laravel Forge
- Necessari per a PWA: Progressive Web Apps

Autenticació Laravel
- Laravel Flavours/Starter Kits
