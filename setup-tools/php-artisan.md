# PHP Artisan

PHP Artisan is a command line interface included with Laravel. Artisan exists at the root of your application as the artisan script and provides a number of helpful commands that can assist you while you build your application. 

- [Laravel PHP Artisan Documentation](https://laravel.com/docs/10.x/artisan)

**Note with Docker:** You must ssh into the container before you can run `php artisan`.

## PHP Artisan Cook Book

Gather all available commands:

```
php artisan list
```

View help screen for a command:

*All commands have a help screen.*

```
php artisan help migrate
```

Make a model:

```
php artisan make:model Listing
```

Make a seeder:

```
php artisan make:seeder SomeSeeder
```

Make a migration:

```
php artisan make:migration create_listings_table
```

Make a factory:

```
php artisan make:factory PostFactory
```

Run migrations:

```
php artisan migrate:refresh
```

Run migrations and seed data:

```
php artisan migrate:refresh —seed
```

Run data seeding:

```
php artisan db:seed
```

Run data seeding for a specific class:

```
php artisan db:seed --class=UserSeeder
```