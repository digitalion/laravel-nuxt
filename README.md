# Digitalion Laravel Nuxt

`laravel-nuxt` was created to offer some sugar when working locally with Laravel+Nuxt, solving some cookie problems in the process. Today, it isn't necessary anymore.

We recommend using [Laravel Sanctum](https://laravel.com/docs/9.x/sanctum), which plays nicely with SPAs (see [Sanctum's SPA Authentication section](https://laravel.com/docs/9.x/sanctum#spa-authentication)). If you can't migrate, just keep using `laravel-nuxt`.

# Laravel Nuxt

This package allows you to build a SPA with Laravel and Nuxt.

## Installation

```bash
composer require digitalion/laravel-nuxt
```

In Laravel 5.5 the service provider will automatically get registered. In older versions of the framework just add the service provider in `config/app.php` file:

```php
return [
  // ...
  'providers' => [
      // ...
      Digitalion\LaravelNuxt\LaravelNuxtServiceProvider::class,
  ],
];
```

You need to add a fallback route that will render the SPA page in `routes/web.php` file:

```php
// ...
// Add this route the last, so it doesn't interfere with your other routes.
Route::get(
    '{uri}',
    '\\'.Digitalion\LaravelNuxt\Controllers\NuxtController::class
)->where('uri', '.*');
```

Finally, you must install the [laravel-nuxt](https://github.com/skyrpex/laravel-nuxt-js) npm package. After following the instructions, run `npm run build` and try your SPA!
