# VUE SENSE NUXT

Es pot utilitzar un hook (pocs exemples trobats per Internet) anomenat serverPrefetch

Qüestions a tenir en compte:
- El codi de serverPrefetch ha de ser asíncron. Utilitzar async/await o tornar una promesa. El servidor esperara a que s'acabi la execució abans de continuar mb el cicle de vida
- Els console.log no sortiran pel navegador. Cal observar la terminal on s'executa npm run dev/npm run start
- Les dades carregades via server prefetch (es mostren durant una estona en un petit flash) poden ser sobreescrites en [alguns casos](https://github.com/vuejs/vue/issues/9906)
- NO cal state loading al navegador ja que les dades ja estaran disponibles

Interessant llegir:
- https://github.com/vuejs/vue/issues/9906

