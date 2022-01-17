# Screencast

TODO URL HERE

# Guió

**Objectiu** repasar opcions autenticació:

1) Aplicació web Laravel: (Cookie Laravel default authentication)

2) SPA

Sense Token
- Aplicació SPA al mateix domini o subdomini: Laravel Sanctum i Cookie Laravel default authentication. Podem provar com s'arregla problema casteaching_package i erros autenticació sense Token o token incorrecte.
- Aplicació SPA en un altre domini: Proxy

Amb Token

En tots aquests casos el sudomini/domini no pot ser el mateix que el backend pq de fet no s'utilitza web. Cal sistema token, tamé Laravel Sanctum
- Aplicacions mòbils
- Aplicacions escriptori

# Casteaching backend

- proves fetes a sanctumSPA
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
