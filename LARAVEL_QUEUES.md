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
