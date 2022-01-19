# Screencasts

- 106 Autenticació, vue router navigation Guards, token Storage i gestió de l'estat (store)

# Vue router Navigation Guards

# State Management

Els components poden tindre dos tipus d'estats (data dels components):

- Estat privat, són variables locals, privades no compartides amb cap altre component.
- Estat compartit, són variables compartides amb altres components (variables globals)

De forma similar al que pasa en la comunicació entre components utilitzant esdeveniments enviats per un EventBus, podem utilitzar un sistema simple creat per nosaltres mateixos o utilitzar una llibreria més complexa com Vuex.

IMPORTANT: El problema de l'estat compartit és el problema general en programació de les variables globals. Son punts d'acoblament del codi, és a dir que el canvi d'estat en un component X pot afectar a un component Y de forma no esperada.

Recursos:
- https://vuejs.org/v2/guide/state-management.html

Exemple d'store sense Vue:
- https://github.com/vueschool/vuejs-router

# Storage

Opcions i multiplataforma:
- Local Storage 
- IndexedDB
- Cookies
- Etc...

Cal tenir en compte que Ionic és un sistema multiplataforma i per tatn és convenient tenir una api comuna per a totes les plataformes de forma que no s'hagui d'esciure codi adaptat a cada plataforma.

La llibreria utilitzada és [ionic-storage](https://github.com/ionic-team/ionic-storage)

<pre>
A simple key-value Storage module for Ionic apps. This utility uses the best storage engine available on the platform without having to interact with it directly (some configuration required, see docs below).
</pre>

Recursos:
- https://ionicframework.com/docs/v5/vue/storage

# Recursos

- https://router.vuejs.org/guide/advanced/navigation-guards.html
- https://vueschool.io/lessons/how-to-configure-an-authentication-middleware-route-guard-with-vue-router?friend=vuerouter
- https://vuejs.org/v2/guide/state-management.html
