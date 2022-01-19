# Continguts previs

De la sèrie:

https://tubeme.acacha.org/tdd

Vídeos:
- [130 Laravel Sanctum Autenticació en aplicacions de tercers utilitzant Laravel com a Backend](https://youtu.be/2QVfuqCVmMc)
- [131 https://youtu.be/j5xDjuzmjAo](https://youtu.be/j5xDjuzmjAo)

# Screencasts

- [106 Autenticació, vue router navigation Guards, user Storage i gestió de l'estat (store)](https://youtu.be/PIdDGCpilK0)
- [107 Autenticació 2. Implementació de la pàgina de Login i Logout amb la API de backend](https://youtu.be/elQEpbzrnsY)

De la sèrie:

https://tubeme.acacha.org/ionic_realworld

![image](https://user-images.githubusercontent.com/4015406/150107523-cfc98434-2e2a-431e-a672-c2046dce4e54.png)

# Codi

- [Final Vídeo 106](https://github.com/acacha/casteachingIonic/commit/1228fe00364480b690662ee8124588e870ea0883): 

# Vue router Navigation Guards

S'utilitzen els Guards per protegir l'accés a rutes, exemple de fitxer de rutes vue:

```javascript

const routes = [
    { path: '/login', component: Login, name: 'login' },
    { path: '/user', component: User, name: 'user', meta: { private: true } },
    { path: '/dashboard', component: Dashboard, name: 'dashboard' },
];

router.beforeEach((to, from, next) => {

        var authenticated = false;
        if ((typeof Storage.get('user') != 'undefined'))
            authenticated = true;

        if (to.meta.private && !authenticated) {
            next({
                name: 'login',
                params: {
                    wantedRoute: to.fullPath,
                },
            })
            return
        }
        next()
    });
```

On Storage representa un estat compartit entre tots els components (que requerirà de persistència i per tant d'alguna base de dades) on guardar si l'usuari està o no logat.

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


# Device name. Native libraries (Capacitor)

Utiltizarem capacitor:

https://capacitorjs.com/docs/apis/device

# AUTENTICATION API BACKEND. LARAVEL SANCTUM

Vegeu també https://github.com/acacha/wiki/blob/main/LARAVEL_SANCTUM.md

La URL explotació és (POST):

https://casteaching.alumnedam.me/api/sanctum/token

Amb les seguents dades:

```
 $request->validate([
            'email' => 'required',
            'password' => 'required',
            'device_name' => 'required',
        ]);
```

# Recursos

- https://router.vuejs.org/guide/advanced/navigation-guards.html
- https://vueschool.io/lessons/how-to-configure-an-authentication-middleware-route-guard-with-vue-router?friend=vuerouter
- https://vuejs.org/v2/guide/state-management.html
