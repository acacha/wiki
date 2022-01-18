# Screencast

- [130. Laravel Sanctum. Autenticació en aplicacions de tercers utilitzant Laravel com a Backend](https://youtu.be/2QVfuqCVmMc)
- [131. Laravel Sanctum. Proporcionant tokens als usuaris amb TDD](https://youtu.be/j5xDjuzmjAo)

De la sèrie TDD:

https://tubeme.acacha.org/tdd

![image](https://user-images.githubusercontent.com/4015406/149905204-d90ca68e-b1f4-4041-bc97-bca321c00a1e.png)

# Currículum

- UF1 Desenvolupament d'aplicacions mòbils del MP8 del mateix nom de segon de DAM (Desenvolupament aplicacions Multiplataforma)

Gràcies a Laravel Sanctum tindrem un sistema que ens permeti utilitzar Laravel com a backend d'autenticació i seguretat (ja sigui utilitzant cookies o Tokens) en aplicacions de tercers. Amb aplicació de tercer ens referim a aplicacions que s'encarreguin del frontend i que no tenen que ser ni aplicacions Laravel ni aplicacions web. Cal tenir en compte que Laravel Sanctum és un únic sistema d'autenticació tant per a aplicacions web Laravel com per a aplicacions web o no web NO Laravel: Aplicació web SPA Javascript (Vanilla, o amb frameworks com Vue, React, Angular, etc.), aplicacions mòbils natíves, híbrides o de qualsevol típus, aplicacions d'escriptori.

# Presentació

 [Docs Laravel](https://laravel.com/docs/8.x/sanctum#introduction)

Gràcies a Laravel Sanctum tindrem un sistema que ens permeti utilitzar Laravel com a backend d'autenticació i seguretat (ja sigui utilitzant cookies o Tokens) en aplicacions de tercers. Amb aplicació de tercer ens referim a aplicacions que s'encarreguin del frontend i que no tenen que ser ni aplicacions Laravel ni aplicacions web. Cal tenir en compte que Laravel Sanctum és un únic sistema d'autenticació tant per a aplicacions web Laravel com per a aplicacions web o no web NO Laravel: Aplicació web SPA Javascript (Vanilla, o amb frameworks com Vue, React, Angular, etc.), aplicacions mòbils natíves, híbrides o de qualsevol típus, aplicacions d'escriptori.

# Guió

**Objectiu** repasar opcions autenticació:

1) Aplicació web Laravel: (Cookie Laravel default authentication)

2) SPA

Sense Token
- Aplicació SPA al mateix domini o subdomini: Laravel Sanctum i Cookie Laravel default authentication. Podem provar com s'arregla problema casteaching_package i erros autenticació sense Token o token incorrecte.
- Aplicació SPA en un altre domini: Proxy

Amb Token

Aplicacions SPA:
- Laravel Jetstream proporciona una UI per a la gestió dels tokens.

En tots aquests casos el sudomini/domini no pot ser el mateix que el backend pq de fet no s'utilitza web. Cal sistema token, tamé Laravel Sanctum
- Aplicacions mòbils
- Aplicacions escriptori

# Casteaching backend

- Proves fetes a sanctumSPA
- Activar middleware EnsureFrontendRequestsAreStateful a Kernel api i comprovar casteachink package funciona
- TODO: video x però posar link a casteaching_package com arreglar problema de token hardcoded

TDD: https://laravel.com/docs/8.x/sanctum#testing
- Implementar [Issuing API Tokens](https://laravel.com/docs/8.x/sanctum#issuing-mobile-api-tokens) amb TDD

El codi ja el tenim (docs de Laravel) però fem abans el test
- Excusa per explicar validació i TDD de validació

Noms de tests:
- email_is_required_for_issuing_tokens
- email_is_valid_for_issuing_tokens
- password_is_required_for_issuing_tokens
- device_name_is_required_for_issuing_tokens
- invalid_email_gives_incorrect_credentials_error
- invalid_password_gives_incorrect_credentials_error
- user_with_valid_credentials_can_issue_a_token


Codi:

```php
Route::post('/sanctum/token', function (Request $request) {
    $request->validate([
        'email' => 'required|email',
        'password' => 'required',
        'device_name' => 'required',
    ]);

    $user = User::where('email', $request->email)->first();

    if (! $user || ! Hash::check($request->password, $user->password)) {
        throw ValidationException::withMessages([
            'email' => ['The provided credentials are incorrect.'],
        ]);
    }

    return $user->createToken($request->device_name)->plainTextToken;
});
```

Com obtenir el device name amb Ionic? 
# Recursos
- https://laravel.com/docs/8.x/sanctum
