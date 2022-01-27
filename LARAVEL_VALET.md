# Coneixements previs
No calen gaires coneixements previs ja que és una eina pensada per ser utilitzada d'una forma molt senzilla. Si que ès veritat però que és interessant:
- Saber que és un substitut per no tenir que crear tot un stack LAMP (Linux Apache Mysql PHP) complet
- Utilitza el servidor web [Nginx](NGINX.md), una alternativa per al servidor web [Apache](Apache.md)
- Utilitza el mòdul PHP FPM, què és el mòdul que permet executar codi PHP incrustat en documents HTML i en servidors web com Nginx o Apache
- La versió oficial és per a MAC però hi ha una versió comunitaria per a Linux que funciona perfectament, que jo conegui no hi ha una versió per a Windows
- Es tracta d'un paquet PHP que s'instal·la globalment utilitzant [Composer](COMPOSER.md)
- Utilitza DnsMasq per mapejar les URL .test a les adreces locals (no són dominis valids a Internet i no poden provocar cap conflicte)
- Serveis per a altres eines no només Laravel fins i tot per estatic HTML

Si que és interessant que tingueu un entorn de desenvolupament amb Ubuntu Desktop. Podeu veure tots els passos a:

https://youtube.acacha.org -> https://www.youtube.com/watch?v=w8j07_DBl_I

# Screencasts

[![Alt text](https://img.youtube.com/vi/ZjVe8W0ozm8/0.jpg)](https://youtu.be/ZjVe8W0ozm8)

# Instal·lació certificats CA

Aneu a la configuració de Chrome seguint els passos de:

https://docs.vmware.com/en/VMware-Adapter-for-SAP-Landscape-Management/2.1.0/Installation-and-Administration-Guide-for-VLA-Administrators/GUID-D60F08AD-6E54-4959-A272-458D08B8B038.html

El certificat que heu d'afegir però són els de la carpeta:

 /PATH_VOSTRA_HOME/.valet/CA // Per exemple /home/sergi/.valet/CA
 
 Escolliu el certificat .pem

# Instal·lació a Linux

https://github.com/cpriego/valet-linux | https://cpriego.github.io/valet-linux/


# Recursos
- https://laravel.com/docs/8.x/valet
- https://github.com/cpriego/valet-linux
- https://cpriego.github.io/valet-linux/
