# PADDLE

Com funciona?

Doncs tenim per a provar una Sandbox i aprendre com va. No podem aplicar per una compte real sinó tenim una empresa real ja que cal passar un procés d'alta no automatitzat
en el qual Paddle analitza riscos i mira si ets o no una empresa o autònom real.

NO es poden utilitzar targetes reals a la Sanbox i per això hi ha una llista de targetes de test:

- **Valid card without 3DS**:	4242 4242 4242 4242
- **Valid card with 3DS**:	4000 0038 0000 0446
- **Declined card**:	4000 0000 0000 0002

Targetes de proves:
- https://developer.paddle.com/getting-started/ZG9jOjIxODY4NjYx-sandbox#test-cards

Configuració:

Al fitxer **.env** file:

```
PADDLE_SANDBOX=true
``` 

Instal·lació paquet composer:

``` 
composer require laravel/cashier-paddle
```

Docs:
- [Sandbox Docs](https://developer.paddle.com/getting-started/ZG9jOjIxODY4NjYx-sandbox)
- https://laravel.com/docs/8.x/cashier-paddle#introduction

# KANUU PACKAGE



Laravel package:
- https://docs.kanuu.io/laravel/redirect-to-kanuu.html#using-the-redirecttokanuu-controller

# Dashboard

![image](https://user-images.githubusercontent.com/4015406/152367316-0176c109-31e0-44cb-9218-9df71dc72a93.png)


# 3DS

3D Secure (3DS) is a protocol that adds extra security to online credit card and debit card payments. It ensures that a form of online identification is added to the authorization of a financial transaction with a credit card. This extra security is based on a 3 domain model of which the name 3D Secure is derived.

# RECURSOS
-  https://laravel.com/docs/8.x/cashier-paddle#introduction
