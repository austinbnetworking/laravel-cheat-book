# Factories/Seeding

[&larr; Home](../README.md)

***

Use Factories & Seeding to create large amounts of test data automatically. Factories make use of the PHPFaker library.

Factories Documentation: [https://laravel.com/docs/10.x/eloquent-factories](https://laravel.com/docs/10.x/eloquent-factories)

Seeding Documentation: [https://laravel.com/docs/10.x/seeding](https://laravel.com/docs/10.x/seeding)

PHPFaker Documentation: [https://fakerphp.github.io/formatters/](https://fakerphp.github.io/formatters/)

## File Locations

- Seeders - `/database/seeders`
- Factories - `/database/factories`

## Factories

Factories describe a set of attributes used by a seeder to create data.

Factories must have a `definition()` method defined that returns values for how a field’s data should be generated.

### Create a new factory:

```php
php artisan make:factory ListingFactory
```

Example File: `/database/factories/ListingFactory.php`

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

With a factory defined, we can use it in our seeder file. 

Default Seeder File: `/database/seeders/DatabaseSeeder.php`

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

Optionally, in our seeder file, we manually define a single set of data using the `create()` method. 

Default Seeder File: `/database/seeders/DatabaseSeeder.php`

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

## Run Seeding

### Seed data:

```php
php artisan db:seed
```

### Seed data for a specific class/factory:

```php
php artisan db:seed --class=UserSeeder
```

### Refresh migrations and seeding:

```php
php artisan migrate:refresh —seed
```