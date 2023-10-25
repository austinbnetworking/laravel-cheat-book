# Laravel Mail

[&larr; Home](../README.md)  

***

- Laravel Mail Documentation: [https://laravel.com/docs/10.x/mail](https://laravel.com/docs/10.x/mail)

Laravel mail is powered by Symfony Mailer and supports sneding mail via SMTP, Mailgun, Postmark, Amazon SES, and sendmail.  

Laravel's email services may be configured via your application's `config/mail.php` configuration file.

### Local Development

Instead of sending your emails, the log mail driver will write all email messages to your log files for inspection.

You will need to clear the configuration cache after updating the environment value. 

```php
php artisan config:cache
```