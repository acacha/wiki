# VUE SENSE NUXT

Es pot utilitzar un hook (pocs exemples trobats per Internet) anomenat [serverPrefetch](https://vuejs.org/api/composition-api-lifecycle.html#onserverprefetch)

Qüestions a tenir en compte:
- El codi de serverPrefetch ha de ser asíncron. Utilitzar async/await o tornar una promesa. El servidor esperara a que s'acabi la execució abans de continuar mb el cicle de vida
- Els console.log no sortiran pel navegador. Cal observar la terminal on s'executa npm run dev/npm run start
- Les dades carregades via server prefetch (es mostren durant una estona en un petit flash) poden ser sobreescrites en [alguns casos](https://github.com/vuejs/vue/issues/9906)
- NO cal state loading al navegador ja que les dades ja estaran disponibles

## SSR i VUEX

S'utilitza per guardar l'estat de les dades obtingudes per serverPrefetch (SSR) i poder reutilitzar-las al client (CSR)

## VUE 2

Oco amb els docs ara per defecte són vue 3. Els podem trobar a https://v2.vuejs.org/v2/guide/ssr.html

## Explicació de data prefetching

https://slides.com/akryum/vue-26-ssr-revolution#/21

You need a solution to store the data resolved on the serve in the rendered HTML page so that the client can pick it up in the browser-side JS

Interessant llegir/Recursos:
- https://github.com/vuejs/vue/issues/9906
- https://slides.com/akryum/vue-26-ssr-revolution#/21
- https://vuejs.org/api/composition-api-lifecycle.html#onserverprefetch
- https://v2.vuejs.org/v2/guide/ssr.html
