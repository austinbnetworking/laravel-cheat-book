# Models

[&larr; Home](../README.md)

***

Laravel uses Eloquent, an object-relational mapper (ORM) that assists in interactions with the database. In Eloquent, each database table has a corresponding Model. The Model object is used to retrieve records, insert records, update records, delete records, etc.

Documentation: [https://laravel.com/docs/10.x/eloquent](https://laravel.com/docs/10.x/eloquent)

## File Location

- `/app/Models`

## Introduction

**Important Note:** You don’t have to tell the Model which table to interact with, the `snake_case`, plural name of the class will be used as the table name unless another name is explicitly specified.

- For example, a `Listing` Model by default interacts with a `listings` database table.
- To explicitly specify the database table, use the `$table` protected variable.

```php
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Database\Eloquent\Model;

class Listing extends Model
{
    use HasFactory;
    /**
    * The table associated with the model.
    *
    * @var string
    */		
    protected $table = 'my_flights';
}
```

## Query Scopes

Query Scopes are useful for searching within/filtering down content that a user may request. Scopes allow us to easily re-use query logic in models. To define a scope, simply prefix a model method with `scope`:

```php
class User extends Model {
 
    public function scopePopular($query)
    {
        return $query->where('votes', '>', 100);
    }
 
    public function scopeWomen($query)
    {
        return $query->whereGender('W');
    }
 
}
```

Then you could use that scope as follows:

```php
$users = User::popular()->women()->orderBy('created_at')->get();
```

Sometimes you may wish to define a scope that accepts parameters. Just add your parameters to your scope function:

```php
class User extends Model {
 
    public function scopeOfType($query, $type)
    {
        return $query->whereType($type);
    }
 
}
```

Then pass the parameter into the scope call:

```php
$users = User::ofType('member')->get();
```

## Usage

### Generate a Model:

```php
php artisan make:model SomeModel
```