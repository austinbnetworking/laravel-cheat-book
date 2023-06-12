# Models

[&larr; Main glossary](README.md)

***

Laravel uses Eloquent, an object-relational mapper (ORM) that assists in interactions with the database. In Eloquent, each database table has a corresponding Model. The Model object is used to retrieve records, insert records, update records, delete records, etc.

Documentation: [https://laravel.com/docs/10.x/eloquent](https://laravel.com/docs/10.x/eloquent)

## File Location

- `/app/Models`

## Models

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

## Usage

### Create a Model:

```php
php artisan make:model SomeModel
```