# Models

[&larr; Home](../README.md)

***

Laravel uses Eloquent, an object-relational mapper (ORM) that assists in interactions with the database. In Eloquent, each database table has a corresponding Model. The Model object is used to retrieve records, insert records, update records, delete records, etc. Eloquent is considered a powerful query builder, at a glance.

Documentation: [https://laravel.com/docs/10.x/eloquent](https://laravel.com/docs/10.x/eloquent)

## File Location

- `/app/Models`

## Introduction

You can create a Eloquent model using PHP Artisan:

```php
php artisan make:model Listing
```

By default, the `snake_case`, plural name of the class will be the default table the model is associated with.

- For example, a `Listing` Model by default interacts with a `listings` database table.
- To explicitly specify the database table, use the `$table` protected variable.

Once the model & database table are both created, you can start leveraging the benefits of Eloquent.

## Accessing Models

Use the `all()` method to retrieve all records in the table. 

```php
use App\Models\Flight;

$flights = Flight::all();

foreach ($flights as $flight) {
    echo $flight->name;
}
```

Use the `get()` method to chain conditions and execute a query. 

```php
use App\Models\Flight;

$flights = Flight::where('active', 1)
               ->orderBy('name')
               ->take(10)
               ->get();

foreach ($flights as $flight) {
    echo $flight->name;
}
```

Use `find()`, `first()`, or `firstWhere()` to get a specific record.

```php
use App\Models\Flight;
 
// Retrieve a model by its primary key...
$flight = Flight::find(1);
 
// Retrieve the first model matching the query constraints...
$flight = Flight::where('active', 1)->first();
 
// Alternative to retrieving the first model matching the query constraints...
$flight = Flight::firstWhere('active', 1);
```

## Local Scope

Local scopes allow you to define common sets of query constraints that you may easily re-use throughout your application.

```php
<?php
 
namespace App\Models;
 
use Illuminate\Database\Eloquent\Builder;
use Illuminate\Database\Eloquent\Model;
 
class User extends Model
{
    /**
     * Scope a query to only include popular users.
     */
    public function scopePopular(Builder $query): void
    {
        $query->where('votes', '>', 100);
    }
 
    /**
     * Scope a query to only include active users.
     */
    public function scopeActive(Builder $query): void
    {
        $query->where('active', 1);
    }
}
```

Then you could use that scope as follows:

```php
use App\Models\User;
 
$users = User::popular()->active()->orderBy('created_at')->get();
```

Sometimes you may wish to define a scope that accepts parameters.

```php
<?php
 
namespace App\Models;
 
use Illuminate\Database\Eloquent\Model;
 
class User extends Model
{
    /**
     * Scope a query to only include users of a given type.
     */
    public function scopeOfType(Builder $query, string $type): void
    {
        $query->where('type', $type);
    }
}
```

Again, use that scope as follows:

```php
use App\Models\User;

$users = User::ofType('admin')->get();
```