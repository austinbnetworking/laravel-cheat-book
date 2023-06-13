# Factories/Seeding

[&larr; Home](../README.md)

***

Seeding a database is a way of creating dummy records in a table for testing purposes. You can seed data directly by manually entering it, or you can build a factory that can handle dummy data generation using the PHPFaker library. 

Factories Documentation: [https://laravel.com/docs/10.x/eloquent-factories](https://laravel.com/docs/10.x/eloquent-factories)

PHPFaker Documentation: [https://fakerphp.github.io/formatters/](https://fakerphp.github.io/formatters/)

## File Locations

- Seeders - `/database/seeders`
- Factories - `/database/factories`

## Factories (Dynamic Data)

We can use factories to seed data, allowing us to create large amounts of test data instantly.

Factories must have a `definition()` method defined that returns values for how a field’s data should be generated. The available faker methods for generating data can be found at the faker libraries documentation page: [https://fakerphp.github.io/formatters/](https://fakerphp.github.io/formatters/)

Once a factory is defined, we can use it in our seeder file. 

File: `/database/factories/ListingFactory.php`

```php
class ListingFactory extends Factory
{
    /**
     * Define the model's default state.
     *
     * @return array<string, mixed>
     */
    public function definition()
    {
        return [
            'title' => $this->faker->sentence(),
            'tags' => 'laravel, api, backend',
            'company' => $this->faker->company(),
            'email' => $this->faker->companyEmail(),
            'website' => $this->faker->url(),
            'location' => $this->faker->city(),
            'description' => $this->faker->paragraph(5),
        ];
    }
}
```

File: `/database/seeders/DatabaseSeeder.php`

*Note: You must import the Model before you can use it’s methods.*

```php
class DatabaseSeeder extends Seeder
{
    /**
     * Seed the application's database.
     *
     * @return void
     */
    public function run()
    {
        Listing::factory(6)->create();
    }
}
```

## Seeding (Manual Data)

In our seeder file, we manually define data using the `create()` method provided to us by our Model. 

File: `/database/seeders/DatabaseSeeder.php`

*Note: You must import the Model before you can use it’s methods.*

```php
Listing::create([
    'title' => 'Listing One',
    'tags' => 'laravel, javascript',
    'company' => 'Some Company',
    'location' => 'Some Location',
    'email' => 'someemail@email.com',
    'website' => 'somewebsite.com',
    'description' => 'Some Description',
]);
```

## Usage

### Seed data:

```php
php artisan db:seed
```

### Seed data for a specific class/factory:

```php
php artisan db:seed --class=UserSeeder
```

### Create a new factory:

```php
php artisan make:factory PostFactory
```

### Refresh migrations and seeding:

```php
php artisan migrate:refresh —seed
```