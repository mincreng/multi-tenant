[![Backers on Open Collective](https://opencollective.com/tenancy/backers/badge.svg)](#backers) 
[![Sponsors on Open Collective](https://opencollective.com/tenancy/sponsors/badge.svg)](#sponsors) 
[![Packagist](https://img.shields.io/packagist/v/hyn/multi-tenant.svg)](https://packagist.org/packages/hyn/multi-tenant)
[![build status](https://circleci.com/gh/hyn/multi-tenant.svg?style=svg)](https://circleci.com/gh/hyn/multi-tenant)
[![codecov](https://codecov.io/gh/hyn/multi-tenant/branch/5.x/graph/badge.svg)](https://codecov.io/gh/hyn/multi-tenant/branch/5.x)
[![Packagist](https://img.shields.io/packagist/dt/hyn/multi-tenant.svg)](https://packagist.org/packages/hyn/multi-tenant)
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/ac3e21d7a5f64e3f87f64c4913c1ca09?branch=4.x)](https://www.codacy.com/app/Luceos/multi-tenant)
[![Join our Discord server](https://discordapp.com/api/guilds/146267795754057729/embed.png)](https://laravel-tenancy.com/chat)
[![Mentioned in Awesome Laravel](https://awesome.re/mentioned-badge.svg)](https://github.com/chiraggude/awesome-laravel)

The unobtrusive Laravel package that makes your app multi tenant. Serving 
multiple websites, each with one or more hostnames from the same codebase. But
with clear separation of assets, database and the ability to override logic per
tenant.

Suitable for marketing companies that like to re-use functionality
for different clients or start-ups building the next software as a
 service.

---

Offers:

- Integration with all Long Term Support versions of Laravel, which includes 5.5.
- Event driven, extensible architecture.  
- Close integration into the webserver.
- The ability to add tenant specific configs, code, routes etc.

Database separation methods:

- One system database and separated tenant databases (default).
- Table prefixed in the system database.
- Or .. manually, the way you want, by listening to an event.

[Complete documentation](https://laravel-tenancy.com) covers more than just the
 installation and configuration.

## Requirements, recommended environment

- Laravel 5.5.
- Linux based OS preferred.
- PHP 7.
- Apache or Nginx.

Please read the full [requirements in the documentation](https://laravel-tenancy.com/documentation/introduction/requirements).

## Installation

```bash
composer require hyn/multi-tenant
```

### Automatic service registration

Using [auto discovery](https://medium.com/@taylorotwell/package-auto-discovery-in-laravel-5-5-ea9e3ab20518), the
tenancy package will be auto detected by Laravel automatically. 

#### Manual service registration

In case you want to disable webserver integration or prefer manual integration, 
set the `dont-discover` in your application composer.json, like so:

```json
{
    "extra": {
        "laravel": {
            "dont-discover": "hyn/multi-tenant"
        }
    }
}
```

If you disable auto discovery you are able to configure the providers by yourself.

Register the service provider in your `config/app.php`:

```php
    'providers' => [
        // [..]
        // Hyn multi tenancy.
        Hyn\Tenancy\Providers\TenancyProvider::class,
        // Hyn multi tenancy webserver integration.
        Hyn\Tenancy\Providers\WebserverProvider::class,
    ],
```

### Deploy configuration

First publish the configuration files so you can modify it to your needs:

```bash
php artisan vendor:publish --tag tenancy
```

Open the `config/tenancy.php` and `config/webserver.php` file and modify to your needs.

> Make sure your system connection has been configured in `database.php`. In case you didn't override the system connection name the `default` connection is used.

Now run:

```bash
php artisan tenancy:install
```
This will run the required system database migrations.

---

## Backers

Thank you to all our backers! 🙏 [[Become a backer](https://opencollective.com/tenancy#backer)]

<a href="https://opencollective.com/tenancy#backers" target="_blank"><img src="https://opencollective.com/tenancy/backers.svg?width=890"></a>


## Sponsors

Support this project by becoming a sponsor. Your logo will show up here with a link to your website. [[Become a sponsor](https://opencollective.com/tenancy#sponsor)]

<a href="https://opencollective.com/tenancy/sponsor/0/website" target="_blank"><img src="https://opencollective.com/tenancy/sponsor/0/avatar.svg"></a>
<a href="https://opencollective.com/tenancy/sponsor/1/website" target="_blank"><img src="https://opencollective.com/tenancy/sponsor/1/avatar.svg"></a>
<a href="https://opencollective.com/tenancy/sponsor/2/website" target="_blank"><img src="https://opencollective.com/tenancy/sponsor/2/avatar.svg"></a>
<a href="https://opencollective.com/tenancy/sponsor/3/website" target="_blank"><img src="https://opencollective.com/tenancy/sponsor/3/avatar.svg"></a>
<a href="https://opencollective.com/tenancy/sponsor/4/website" target="_blank"><img src="https://opencollective.com/tenancy/sponsor/4/avatar.svg"></a>
<a href="https://opencollective.com/tenancy/sponsor/5/website" target="_blank"><img src="https://opencollective.com/tenancy/sponsor/5/avatar.svg"></a>
<a href="https://opencollective.com/tenancy/sponsor/6/website" target="_blank"><img src="https://opencollective.com/tenancy/sponsor/6/avatar.svg"></a>
<a href="https://opencollective.com/tenancy/sponsor/7/website" target="_blank"><img src="https://opencollective.com/tenancy/sponsor/7/avatar.svg"></a>
<a href="https://opencollective.com/tenancy/sponsor/8/website" target="_blank"><img src="https://opencollective.com/tenancy/sponsor/8/avatar.svg"></a>
<a href="https://opencollective.com/tenancy/sponsor/9/website" target="_blank"><img src="https://opencollective.com/tenancy/sponsor/9/avatar.svg"></a>


---

## License and contributing

This package is offered under the [MIT license](license.md). In case you're interested at
contributing, make sure to read the [contributing guidelines](.github/CONTRIBUTING.md).

### Testing

Run tests using (not recommended when using MySQL database driver):

```bash
vendor/bin/phpunit
```

Please note this will create an enormous number of tenant databases. You can easily remove these by
running the bash script to clean the local databases that follow the same naming convention as this
package:

```bash
bash tests/scripts/clean-local-dbs.sh
```

> Please be warned this will reset your current application completely, dropping tenant and system
databases and removing the tenancy.json file inside the Laravel directory.

## Changes

All changes are covered in the [changelog](changelog.md).

## Contact

Get in touch personally using;

- The email address provided in the [composer.json](composer.json).
- [Discord chat](https://laravel-tenancy.com/chat).

Keep informed about news of this package by [signing up for the newsletter](https://laravel-tenancy.com/newsletter/signup).
