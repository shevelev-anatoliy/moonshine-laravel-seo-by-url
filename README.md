### Prolog

Seo data is stored in the database in the `seo` table and
is linked to pages based on the url, the url is unique for websites, therefore, the seo in this package is built from it

- Easy to use
- Not tied to entities
- All data is cached relative to url and reset by events on the model

### Installation

```shell
composer require lee-to/laravel-seo-by-url
```

### MoonShine

if you use the [MoonShine](https://moonshine.cutcode.ru), then publish the resource with this command

```shell
php artisan seo:moonshine
```

### Get started

For starters, you can choose the best usage approach for you:

- Facade
```php
use Leeto\Seo\Seo;

// ...

Seo::title('Hello world')
```

- Helper
```php
seo()->title('Hello world')
```

- DI
```php
use Leeto\Seo\SeoManager;

// ...

public function __invoke(SeoManager $seo)
{
    //
}
```


* Ok I prefer to use the helper

### Blade directives

#### Render meta tags
title, descriptions, keywords, og

```html
<html>
<head>
    <!-- // .. -->

    @seo

    <!-- // .. -->
</head>
```

#### Render seo text

```html
<div>
    @seoText('Default text')
</div>
```

### Set and save seo data

- set

```php
seo()->title('Im page title')
```

- set and save in database

```php
seo()->title('Im page title', true)
```

- other tags

```php
seo()->description('Im page description')
seo()->keywords('Im page description')
seo()->text('Im page description')
seo()->og(['image' => 'link to image'])
```

- get value

```php
seo()->meta()->title()
seo()->meta()->description()
seo()->meta()->keywords()
seo()->meta()->text()
seo()->meta()->og()
```


- get html tags

```php
seo()->meta()->html()
```

- save by model

```php
use Leeto\Seo\Models\Seo;

Seo::create([
    'url' => '/',
    'title' => 'Im title'
]);
```

### Default values

Set in seo config `config/seo.php`

```php
return [
    'default' => [
        'title' => 'Im title'
    ]
]);
```