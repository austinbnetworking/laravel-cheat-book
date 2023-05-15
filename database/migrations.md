# Migrations

Laravel allows us to define and share an application's database schema definition. Each migration contains a timestamp to determine the order.

- [Laravel Migration Documentation](https://laravel.com/docs/10.x/migrations)

## File Locations

- `/database/migrations`

## Migrations

Each migration must contain `up()` and `down()` methods. This is how the tables are created when running migrations, and how they are deleted when rolled back.

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

## Usage

### Create migration:

```
php artisan make:migration create_listings_table
```

- By default, the class will map to the database table based on file naming:
    - For `create_listings_table`, the default table is `listings`.

### Run migrations:

```
php artisan migrate
```

### Refresh migrations and seeding:

```
php artisan migrate:refresh —seed
```