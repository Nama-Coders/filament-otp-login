# OTP Login for FilamentPHP

This package is an OTP Login for FilamentPHP. It is a simple package that allows you to login to your FilamentPHP application using OTP. This package was forked from afsakar/filament-otp-login with auth guard addition

## Installation

You can install the package via composer:

```bash
composer require namacoders/filament-otp-login
```

You can publish and run the migrations with:

```bash
php artisan vendor:publish --tag="filament-otp-login-migrations"
php artisan migrate
```

You can publish the config and translations files with:

```bash
php artisan vendor:publish --tag="filament-otp-login-config"
php artisan vendor:publish --tag="filament-otp-login-translations"
```

Optionally, you can publish the views using

```bash
php artisan vendor:publish --tag="filament-otp-login-views"
```

This is the contents of the published config file:

```php
return [
    'table_name' => 'otp_codes', // Table name to store OTP codes
    'guard' => 'web',
    'otp_code' => [
        'length' => env('OTP_LOGIN_CODE_LENGTH', 6), // Length of the OTP code
        'expires' => env('OTP_LOGIN_CODE_EXPIRES_SECONDS', 120), // Expiration time of the OTP code in seconds
    ],
];

```

## Usage

Just register the `Namacoders\FilamentOtpLogin\FilamentOtpLoginPlugin` plugin in the your panel provider file.

```php
use Namacoders\FilamentOtpLogin\FilamentOtpLoginPlugin;

    public function panel(Panel $panel): Panel
    {
        return $panel
            ->plugins([
                FilamentOtpLoginPlugin::make(),
            ]);
    }
```

_*Note:* For medium and large scale applications, you only need to run "php artisan model:prune" command as cron to prevent the otp_code table from bloating and performance issues._

## Testing

```bash
composer test
```

## Changelog

Please see [CHANGELOG](CHANGELOG.md) for more information on what has changed recently.

## Contributing

Please see [CONTRIBUTING](.github/CONTRIBUTING.md) for details.

## Security Vulnerabilities

Please review [our security policy](../../security/policy) on how to report security vulnerabilities.

## Credits

- [Azad Furkan ŞAKAR](https://github.com/afsakar)
- [Abd AlRahman](https://github.com/namacoders)
- [All Contributors](../../contributors)
- [OTP Input inspiration](https://github.com/rajeshdewle/otp-pin-using-alpine-js-and-tailwindcss)

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
