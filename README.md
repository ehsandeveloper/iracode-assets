# Laravel Assets management

[![Latest Version](https://img.shields.io/github/release/iracode/laravel-assets.svg?style=flat-square)](https://github.com/iracode/laravel-assets/releases)
[![Software License](https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square)](LICENSE.md)
[![Build Status](https://img.shields.io/travis/iracode/laravel-assets/master.svg?style=flat-square)](https://travis-ci.org/iracode/laravel-assets)
[![Quality Score](https://img.shields.io/scrutinizer/g/iracode/laravel-assets.svg?style=flat-square)](https://scrutinizer-ci.com/g/iracode/laravel-assets)
[![StyleCI](https://styleci.io/repos/154250020/shield)](https://styleci.io/repos/154250020)
[![Total Downloads](https://img.shields.io/packagist/dt/iracode/assets.svg?style=flat-square)](https://packagist.org/packages/iracode/assets)
[![Maintainability](https://api.codeclimate.com/v1/badges/a6e4612307e3b3bf8252/maintainability)](https://codeclimate.com/github/iracode/laravel-assets/maintainability)

## Installation

```bash
composer require iracode/assets
```

For version <= 5.4:

Add to section `providers` of `config/app.php`:

```php
// config/app.php
'providers' => [
    ...
    Iracode\Assets\Providers\AssetsServiceProvider::class,
];
```

And add to `aliases` section:

```php
// config/app.php
'aliases' => [
    ...
    'Assets' => Iracode\Assets\Facades\AssetsFacade::class,
];
```

All assets resource will be manage in config file so we need to publish config to use.

```bash
php artisan vendor:publish --provider="Iracode\Assets\Providers\AssetsServiceProvider" --tag=config
```

Add to your master layout view, in `head` tag:

```php
{!! \Assets::renderHeader() !!}
```

and before `body` tag close:

```php
{!! \Assets::renderFooter() !!}
```

## Methods

### Add scripts

```php
\Assets::addScripts(['key-of-assets-in-config-file']);
```

Example:

```php
\Assets::addScripts(['app', 'bootstrap', 'jquery']);
```

### Add styles

```php
\Assets::addStyles(['key-of-assets-in-config-file']);
```

Example:

```php
\Assets::addStyles(['bootstrap', 'font-awesome']);
```

### Remove scripts

```php
\Assets::removeScripts(['key-of-assets-in-config-file']);
```

Example:

```php
\Assets::removeScripts(['bootstrap']);
```

### Remove styles

```php
\Assets::removeStyles(['key-of-assets-in-config-file']);
```

Example:

```php
\Assets::removeStyles(['font-awesome']);
```

### Others

- Set version for assets. Add to `.env`

```bash
ASSETS_VERSION=1.0
```

Then all assets will be added `?v=1.0`

- Change to online mode

```bash
ASSETS_OFFLINE=false
```

Then assets will be loaded from CDN if it's defined in config file.

- To disable versioning:

```bash
ASSETS_ENABLE_VERSION=false
```

## Contributors

- [EhsanOfficial](https://github.com/esf495)
