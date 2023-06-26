# Migrations

[&larr; Home](../README.md)

***

Laravel allows us to define and share an application's database schema definition. Each migration contains a timestamp, which is used when determining the order of operations.

Documentation: [https://laravel.com/docs/10.x/migrations](https://laravel.com/docs/10.x/migrations)

## File Locations

- `/database/migrations`

## Define a Migration

Each migration must contain `up()` and `down()` methods. The up method is how we instantiate columns/data/indexes and the down method is how we delete them. 

After generating a migration, we define it's structure using Laravel's schema facade. 

A list of available column types & column modifiers can be found here:

[https://laravel.com/docs/10.x/migrations#available-column-types](https://laravel.com/docs/10.x/migrations#available-column-types)

[https://laravel.com/docs/10.x/migrations#column-modifiers](https://laravel.com/docs/10.x/migrations#column-modifiers)

To generate a migration:

```php
php artisan make:migration create_listings_table
```

- By default, the class will map to the database table based on this naming convention:
    - For `create_listings_table`, the default table is `listings`.

Example File: `2023_07_20_120000_create_listings_table.php`

```php
return new class extends Migration
{
    /**
     * Run the migrations.
     *
     * @return void
     */
    public function up()
    {
        Schema::create('listings', function (Blueprint $table) {
            $table->id();
            $table->string('title');
            $table->string('tags');
            $table->string('company');
            $table->string('location');
            $table->string('email');
            $table->string('website');
            $table->longText('description');
            $table->timestamps();
        });
    }

    /**
     * Reverse the migrations.
     *
     * @return void
     */
    public function down()
    {
        Schema::dropIfExists('listings');
    }
};
```

## Running Migrations

Run all outstanding migrations
```php
php artisan migrate
```

Get a migration status
```php
php artisan migrate:status
```

Rollback the last migration
```php
php artisan migrate:rollback
```

Rollback all migrations
```php
php artisan migrate:reset
```

Rollback & migrate
```php
php artisan migrate:refresh
```

Rollback & migrate & seed
```php
php artisan migrate:refresh —seed
```