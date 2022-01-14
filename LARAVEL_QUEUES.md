# Screencast

- [129 Cuas Laravel](https://youtu.be/bnzM_Yuj6Qg): https://youtu.be/bnzM_Yuj6Qg
- Video [127 Notificacions per email](https://youtu.be/8oAcBl63Pvg). Enviament d'una notificació a administradors informant que s'ha creat un vídeo nou. 
- Video [128 Events Laravel i TDD amb Mocking. Afegir funcionalitats a codi existent](https://youtu.be/AUWTpfH-M44). Afegir funcionalitat enviament email a codi existent amb codi net utilitzant events i Listeners. Com fer-ho amb TDD i com aillar els testos amb mocks i fakes.

# Codi resultant:

https://github.com/acacha/casteaching/commit/ee8cc214dd5add14f0c30ce98e48a6baf69d0c86

# Canvis en l'entorn (vostre màquian local)

Cal tenir redis instal·lat i en execució:

```
// Comprovació port tancat
nmap -p 6379 localhost 
//Instal·lació
sudo apt-get install redis-server
sudo apt-get install php-redis
//comprovació port obert:
nmap -p 6379 localhost 
// Comproveu s'està executant:
ps aux | grep redis-server
redis-cli
127.0.0.1:6379> exit
```

Que cal que comproveu si alguna cosa us falla:

**Instalació, execució  i configuració de supervisor**

Només en local! En explotació ho feu amb laravel Forge

Instal·leu i/comproveu està instal.lat

```bash
sudo apt-get install supervisor
dpkg -l | grep supervisor
ps aux | grep supervisord
```

Fitxers de configuració, carpeta **/etc/supervisor/conf.d/**, fitxer **/etc/supervisor/conf.d/laravel-worker.conf**:

```
[program:laravel-worker]
process_name=%(program_name)s_%(process_num)02d
command=php /home/sergi/Code/acacha/casteaching/artisan queue:work redis --sleep=3 --tries=3 --max-time=3600
autostart=true
autorestart=true
stopasgroup=true
killasgroup=true
user=sergi
numprocs=8
redirect_stderr=true
stdout_logfile=/home/sergi/Code/acacha/casteaching/storage/logs/worker.log
stopwaitsecs=3600
```

Atenció: canvie el nom d'usuari al que us pertoqui (no poseu acacha) i comproveu que existeix el fitxer /home/sergi/Code/EL_VOSTRE_USUARI/casteaching/storage/logs/worker.log.

El pujo també al codi de Github:

https://github.com/acacha/casteaching/blob/main/supervisor/laravel-worker.conf

Per comprovar que funciona ok heu de comprovar que hi ha 8 procesos en funcionament:

```
ps aux | grep queue:work 
sergi      25398  0.0  0.2 113636 46140 ?        S    12:28   0:00 php /home/sergi/Code/acacha/casteaching/artisan queue:work redis --sleep=3 --tries=3 --max-time=3600
sergi      25429  0.0  0.2 113636 46048 ?        S    12:28   0:00 php /home/sergi/Code/acacha/casteaching/artisan queue:work redis --sleep=3 --tries=3 --max-time=3600
sergi      25438  0.0  0.2 113636 46252 ?        S    12:28   0:00 php /home/sergi/Code/acacha/casteaching/artisan queue:work redis --sleep=3 --tries=3 --max-time=3600
sergi      25439  0.0  0.2 113636 46124 ?        S    12:28   0:00 php /home/sergi/Code/acacha/casteaching/artisan queue:work redis --sleep=3 --tries=3 --max-time=3600
sergi      25440  0.0  0.2 113636 46216 ?        S    12:28   0:00 php /home/sergi/Code/acacha/casteaching/artisan queue:work redis --sleep=3 --tries=3 --max-time=3600
sergi      25441  0.0  0.2 113636 45612 ?        S    12:28   0:00 php /home/sergi/Code/acacha/casteaching/artisan queue:work redis --sleep=3 --tries=3 --max-time=3600
sergi      25442  0.0  0.2 113636 45920 ?        S    12:28   0:00 php /home/sergi/Code/acacha/casteaching/artisan queue:work redis --sleep=3 --tries=3 --max-time=3600
sergi      25443  0.0  0.2 113636 46124 ?        S    12:28   0:00 php /home/sergi/Code/acacha/casteaching/artisan queue:work redis --sleep=3 --tries=3 --max-time=3600
sergi      28118  0.0  0.0  17712  2500 pts/1    S+   12:43   0:00 grep --color=auto --exclude-dir=.bzr --exclude-dir=CVS --exclude-dir=.git --exclude-dir=.hg --exclude-dir=.svn --exclude-dir=.idea --exclude-dir=.tox queue:work
```


# CUAS LARAVEL

Permeten diferir l'execució de tasques potencialment intensives, és a dir que poden tardar massa temps per a ser executades en una petició web regular sense afectar a la 
percepció que té l'usuari de rendiment de la nostra aplicació. Entrem en qüestions de rendiment i de User Experience.

Exemples de tasques intesives:
- Uploading de fitxers grans
- Parsing
- Procesament de fitxers
- Crides a APis externes
- Etc

Es proporciona una API comuna per a treballar en múltiples implementacions (drivers) de cuas com Amazon, Redis, Beanstalkd, etc

# Tasca casteaching

Video 129
- **Objectiu**: Executar de forma asíncrona l'enviament de la notificació VideoCreated
- Explicació de les cues: Driver extern o driver propi -> Driver propi cal configurar supervisor
- Configuració de les cuas i del driver
- Queued Event Listeners: https://laravel.com/docs/8.x/events#queued-event-listeners
- Configuració en explotació: enviament emails i cuas. Laravel Forge
- Merge a explotació i penjar codi a servidor en explotació amb Laravel Forge
- SSL del servidor explotació?

# Currículum

- UF2 del mòdul MP9 (Processos i Serveis):  UF2 és la UF de processos, separació del codi en multiples mòduls que es poden executar concurrenment o linealment.
  - Amb Laravel i PHP utilitzarem les Cues o Jobs
  - També necessitem aprendre a realitzar tasques que siguin potencialment llargues en el temps com utilitzar APIs de tercers, upload de fitxers o enviar emails/notificacions.

# RECURSOS

https://laravel.com/docs/8.x/queues
