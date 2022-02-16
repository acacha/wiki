---
title: Laravel Cashier
description: Pagaments amb Laravel Cashier. Stripe i Paddle
extends: _layouts.documentation
section: content
---

# LARAVEL CASHIER

# Screencast

- [Laravel Cashier amb Paddle i Kanuu](https://youtu.be/htQSnV-TMIE)

## Resum de canvis

Branca [laravel_cashier_paddle](https://github.com/acacha/casteaching/tree/laravel_cashier_paddle)

**Canvis**:

Fitxer composer.json paquets: 

- [kanuu-io/kanuu-laravel](https://packagist.org/packages/kanuu-io/kanuu-laravel) i [laravel/cashier-paddle](laravel/cashier-paddle)

Ruta de Kanuu a **routes/web.php**

```php
Kanuu::redirectRoute()
    ->middleware('auth')
    ->name('kanuu.redirect');
```    

# CASTEACHING

Múltiples opcions:
- Paddle Sandbox. Configurar els productes de subscripció i de pagament en un sol cop
- Configuració de Paddle i Laravel Cashier i Kanuu
- Usuaris ja logats: Boto de gestionar la seva subscripció i pagaments -> Billing -> Utilitzar servei extern Kanuu
- Usuaris no logats: primer reenviar al login i després poder gestionar la subscripció
- Landing Page: Taula de preus utilitzant Tailwind UI: [Taules de preus Tailwind UI](https://tailwindui.com/components/marketing/sections/pricing)
- Provider KanuuProvider.php afegit a **config/app.php**
- Registrar al provider els listeners Kanuu::on('subscription_created', function ($payload, $identifier) {// Create a new subscription in your application...});
- Utilitzar el Boilerplate/publish de Kanuu que crea una taula de subscripció per associar subscripcions a usuaris: 
Recursos:
- [Taules de preus Tailwind UI](https://tailwindui.com/components/marketing/sections/pricing)

# PADDLE

Com funciona?

Doncs tenim per a provar una [Sandbox](https://sandbox-vendors.paddle.com/signup) i aprendre com va. No podem aplicar per una compte real sinó tenim una empresa real ja que cal passar un procés d'alta no automatitzat
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
- https://sandbox-vendors.paddle.com/signup

## Paddle Sanbox

https://sandbox-vendors.paddle.com/signup

## KANUU PACKAGE

Laravel package:
- https://docs.kanuu.io/laravel/redirect-to-kanuu.html#using-the-redirecttokanuu-controller

# Dashboard

![image](https://user-images.githubusercontent.com/4015406/152367316-0176c109-31e0-44cb-9218-9df71dc72a93.png)


# 3DS

3D Secure (3DS) is a protocol that adds extra security to online credit card and debit card payments. It ensures that a form of online identification is added to the authorization of a financial transaction with a credit card. This extra security is based on a 3 domain model of which the name 3D Secure is derived.

# Protecció/Accés a recursos segons l'estat de subscripció de l'usuari

Opcions:

## Paddle's webhooks

Documentació:

- Les URL dels webhooks han de ser públiques! per a testejar en local cal utilitzar ngrok
- Cal tenir al fitxer .env la paddle public key posada correctament.
- Cal posar a les routes web (fitxer **routes/web.php**): Kanuu::webhookRoute('webhooks/paddle')
- A Developers Tools/ Events
- Desactivar CSRF per a webhooks a **VerifyCsrfToken middleware**.

```php
protected $except = [
    'webhooks/*',
];
```

Docs:
- [Paddle's webhooks](https://docs.kanuu.io/getting-started/integrating-kanuu.html#using-paddle-s-webhooks)
- https://docs.kanuu.io/laravel/webhook-helpers.html#_2-register-the-webhook-route

## Kanuu Subscription API

[Kanuu Subscription API](https://docs.kanuu.io/getting-started/integrating-kanuu.html#subscription-api)

## Política de subscripcions

Qüestions a tenir en compte:
- El usuari (i potser més endavant els teams de l'usuari) determinen l'estat de la subscripió (taula subscriptions)
Nivells:
- Pot ser per vídeos o per series

Vídeos:
- Vídeos públics: en cas que un vídeo sigui public però la sèrie privada el vídeo serà public. Mana el vídeo com a nivell de concreció més alt
- Vídeos privats: per poder accedir cal
  - Tenir un pla de subscripció mensual actiu o
  - Tenir una one time purchase associada a aquell vídeo
  - O tenir una one time purchase associada a la sèrie
- Serìes publiques
  - Tots els vídeos seràn publics per defecte excepte que s'indiqui lo contrari. Sempre mana vídeo
- Series privades
  -  Tots els vídeos seràn privats per defecte (requereixens de subscripció) excepte que es marqui el vídeo específicament com a pùblic
Camp calculat associat a un video
- subscriptionNeeded -> Torna un false per defecte (videos publics) i  depenen si cal comprovar o no subscripció
- Cal implementar tota la lògica aquí segons lo comentat prèviament:
- Primer check -> Video privat -> return necesitaSubscripció
- Segons check -> Video null (no especificat si és privat o no) però serie privada -> return Necessita subscripció
- últim check: usuaris està subscrit pla mensual o pla anual -> 
- Valor final -> valor per defecte -> no necessita subscripció
Cal marcar els vídeos com a publics o privats
- Nou camp data booleà
- one_time_purchase_id: nullable -> Si no és null indica la one time purchase que dona accés al vídeo
Cal marcar les seies com a publics o privats
- Nou camp data booleà
- one_time_purchase_id: nullable -> Si no és null indica la one time purchase que dona accés a la seie
 
Que cal crear a paddle:
- Un one time purchase per cada vídeo privat
- Un one time purchase per cada sèrie privada
- Subscripció anual
- Subscripció mensual

# RECURSOS
-  https://laravel.com/docs/8.x/cashier-paddle#introduction
- https://tailwindui.com/components/marketing/sections/pricing
