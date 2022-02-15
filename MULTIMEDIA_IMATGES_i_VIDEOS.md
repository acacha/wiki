# Screencasts

# Continguts Previs

- [Laravel File Uploads](https://github.com/acacha/wiki/blob/main/LARAVEL_FILE_UPLOADS.md)
- [Upgrade a Laravel 9](https://github.com/acacha/wiki/blob/main/LARAVEL_9.md)

# Imatges, file uploads i Laravel. Presentació

Com passar d'una UI:

![image](https://user-images.githubusercontent.com/4015406/153841300-7c8f6d55-ea17-4073-9730-6cfef05283df.png)

A:

![image](https://user-images.githubusercontent.com/4015406/154020586-045ebd31-56d2-4ee6-b010-5369677e9c13.png)

Qüestions a tenir en compte:
- Quan les imatges poden ser nullables (per tant la imatge és opcional). Quina imatge mostrar quan no hi ha imatge?
- Múltiple solucions: (UI Avatars)[https://eu.ui-avatars.com/] utilitza les inicials del nom usuari
- Gravatar: utilitzar la imatge de Gravatar(WordPress)
- https://www.producthunt.com/alternatives/ui-faces | https://github.com/topics/avatars
- Github: Identicons: https://github.blog/2013-08-14-identicons/
- https://barro.github.io/2018/02/avatars-identicons-and-hash-visualization/
- https://github.com/download13/blockies

# Guió 

Primer us mostro els canvis realitzats a la branca [millores_ui_fileuploads](https://github.com/acacha/casteaching/tree/millores_ui_fileuploads) branca que juntarem (merge) amb main.

Mostrar una imatge per defecte quan no hi ha imatge associada a la serie com:

![Blue Elegant Minimalist Gadget Review YouTube Thumbnail](https://user-images.githubusercontent.com/4015406/153844292-743d51e5-3534-49fe-9c38-4f328512b3b7.png)

En comptes de:

![image](https://user-images.githubusercontent.com/4015406/153844532-680f1138-5107-455b-b68f-1340ee84db09.png)

I el mateix amb el teacher. Utilitzem un avatar per defecte per als usuaris anònims:

https://avatars.dicebear.com/api/identicon/:seed.svg

Exemple:

![image](https://user-images.githubusercontent.com/4015406/154021315-9ea941f8-51ea-4120-90b7-c583f6e91e26.png)



# Optimització imatges

# Recursos
- [Curs TDD Adam Wathan i optimització Imatges amb  ](https://course.testdrivenlaravel.com/lessons/module-28/testing-events#143)

# blur hashing images

https://blur-hash.com/#/
