# Laravel Postmark

[![Latest Version on Packagist][ico-version]][link-packagist]
[![Software License][ico-license]](LICENSE.md)
[![Build Status][ico-travis]][link-travis]
[![Coverage Status][ico-scrutinizer]][link-scrutinizer]
[![Quality Score][ico-code-quality]][link-code-quality]
[![Total Downloads][ico-downloads]][link-downloads]

## Install

Via Composer

``` bash
$ composer require coconutcraig/laravel-postmark
```

## Usage

In order to take advantage of the Postmark mail driver, we need to **replace** the existing `MailServiceProvider` in `config/app.php`. Find this line:

``` php
Iluminate\Mail\MailServiceProvider::class,
```

And **replace** it with:

```php
Coconuts\Mail\MailServiceProvider::class,
```

Next we will need to update the `config/services.php` file to hold our Postmark specific config.

```php
return [
    // ...
    
    'postmark' => [
        'secret' => env('POSTMARK_SECRET'),    
    ],
];
```

Then we can add the server key to our `.env` file and update our `MAIL_DRIVER`.

```php
MAIL_DRIVER=postmark

// ...

POSTMARK_SECRET=YOUR-SERVER-KEY-HERE
```

That's it! The mail system continues to work the exact same way as before and you can switch out Postmark for any of the pre-packaged Laravel mail drivers (smtp, mailgun, log, etc...).

> Remember, when using Postmark the sending address used in your emails must be a [valid Sender Signature](http://support.postmarkapp.com/category/45-category) that you have already configured.

## Change log

Please see [CHANGELOG](CHANGELOG.md) for more information on what has changed recently.

## Testing

``` bash
$ composer test
```

## Contributing

Please see [CONTRIBUTING](CONTRIBUTING.md) and [CONDUCT](CONDUCT.md) for details.

## Security

If you discover any security related issues, please email craig.paul@coconutcalendar.com instead of using the issue tracker.

## Credits

- [Craig Paul][link-author]
- [All Contributors][link-contributors]

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.

[ico-version]: https://img.shields.io/packagist/v/coconutcraig/laravel-postmark.svg?style=flat-square
[ico-license]: https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square
[ico-travis]: https://img.shields.io/travis/coconutcraig/laravel-postmark/master.svg?style=flat-square
[ico-scrutinizer]: https://img.shields.io/scrutinizer/coverage/g/coconutcraig/laravel-postmark.svg?style=flat-square
[ico-code-quality]: https://img.shields.io/scrutinizer/g/coconutcraig/laravel-postmark.svg?style=flat-square
[ico-downloads]: https://img.shields.io/packagist/dt/coconutcraig/laravel-postmark.svg?style=flat-square

[link-packagist]: https://packagist.org/packages/coconutcraig/laravel-postmark
[link-travis]: https://travis-ci.org/coconutcraig/laravel-postmark
[link-scrutinizer]: https://scrutinizer-ci.com/g/coconutcraig/laravel-postmark/code-structure
[link-code-quality]: https://scrutinizer-ci.com/g/coconutcraig/laravel-postmark
[link-downloads]: https://packagist.org/packages/coconutcraig/laravel-postmark
[link-author]: https://github.com/coconutcraig
[link-contributors]: ../../contributors
