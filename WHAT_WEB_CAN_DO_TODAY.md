# Casteaching

**Contacts API**
- Enviar invitació a un usuari, escollir email dels contactes
- Crear usuaris a partir dels contactes, permet seleccionar múltiples però no tots de cop

**Share api: https://whatwebcando.today/sharing.html**
- Botó per compartir video o serie -> Només Chrome Android
- Idea share API -> Per agafar vídeos deyoutube. al fer un share i posar-ho a casteaching que agafi la URL, etl titol i tot per crear una nova entrada a casteaching
  - Parser/share de vídeos de Youtube ja existents?
- Foreground api: aturar la reproducció de videos un cop s'ha canviat de pestanya

# Foreground Detection

Recursos:
- http://daniemon.com/tech/webapps/page-visibility/
- https://medium.com/nerd-for-tech/page-visibility-api-630c230f9efd

# PWA

Moltes de les funcionalitats de what web can do today les veiem a PWA:
- Manifest file
- Service Workers
- Offline support
- Push notifications
- Background Sync 

# METATAGS 

Full example:

```
<!-- Primary Meta Tags -->
<title>Meta Tags — Preview, Edit and Generate</title>
<meta name="title" content="Meta Tags — Preview, Edit and Generate">
<meta name="description" content="With Meta Tags you can edit and experiment with your content then preview how your webpage will look on Google, Facebook, Twitter and more!">

<!-- Open Graph / Facebook -->
<meta property="og:type" content="website">
<meta property="og:url" content="https://metatags.io/">
<meta property="og:title" content="Meta Tags — Preview, Edit and Generate">
<meta property="og:description" content="With Meta Tags you can edit and experiment with your content then preview how your webpage will look on Google, Facebook, Twitter and more!">
<meta property="og:image" content="https://metatags.io/assets/meta-tags-16a33a6a8531e519cc0936fbba0ad904e52d35f34a46c97a2c9f6f7dd7d336f2.png">

<!-- Twitter -->
<meta property="twitter:card" content="summary_large_image">
<meta property="twitter:url" content="https://metatags.io/">
<meta property="twitter:title" content="Meta Tags — Preview, Edit and Generate">
<meta property="twitter:description" content="With Meta Tags you can edit and experiment with your content then preview how your webpage will look on Google, Facebook, Twitter and more!">
<meta property="twitter:image" content="https://metatags.io/assets/meta-tags-16a33a6a8531e519cc0936fbba0ad904e52d35f34a46c97a2c9f6f7dd7d336f2.png">
```

Generator:
- https://metatags.io/

# SEO TAGS

```html
<meta name="title" content="Un lloc de la hostia">
<meta name="description" content="dsa as das dasdasd asd as d">
<meta name="keywords" content="prova1">
<meta name="robots" content="index, follow">
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<meta name="language" content="English">
```

# Canonical URL

Són clau per al SEO i per tant per pàgines publiques.

Permeten identificar URLS que són de la mateix pàgina pero només amb petits canvis com canvis a la query String

- https://www.bbclothing.co.uk/en-gb/clothing/shirts.html
- https://www.bbclothing.co.uk/en-gb/clothing/shirts.html?Size=XL

Per a Google són dos pàgines diferents quan realment el seu canonical URL és: https://www.bbclothing.co.uk/en-gb/clothing/shirts.html

Resources:
- https://ahrefs.com/blog/canonical-tags/

# Metatags

**Open Graphs Meta tags**

Example:

```
<meta property="og:title" content="How to Become an SEO Expert (8 Steps)" />
<meta property="og:description" content="Get from SEO newbie to SEO pro in 8 simple steps." />
<meta property="og:image" content="https://ahrefs.com/blog/wp-content/uploads/2019/12/fb-how-to-become-an-seo-expert.png" />
```

Recursos:
- https://ahrefs.com/blog/open-graph-meta-tags/
- https://ogp.me/

**Images**

Image: You need to select the image you want to share, and you need to make sure it’s cropped to fit properly. Don’t select a portrait image unless you crop it to the exact proportions first, otherwise the social networks will crop the image for you, and not always in the best way.

What size should your images be?

- Facebook: 1200 X 630 pixels
- Twitter: 1200 X 675 pixels
- LinkedIn: 1200 X 627 pixels
- Instagram: només permet compartir imatges

## Twitter Cards

# Share API

Abans es bona idea preparar tots els meta tags a head per facilitar compartició a Xarxes socials?

També es pot utilitzr per registrar la app com un target de share

Recursos:
- https://web.dev/web-share/
- https://developer.mozilla.org/en-US/docs/Web/API/Navigator/share
- https://whatwebcando.today/sharing.html

# Recursos 
- https://whatwebcando.today/
