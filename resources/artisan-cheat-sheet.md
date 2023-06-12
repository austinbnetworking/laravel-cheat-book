# PHP Artisan Cheat Sheet

PHP Artisan is a command-line interface (CLI) tool that comes with the Laravel PHP framework. 

**Note with Docker:** You must SSH into the CLI container in order to run artisan commands against your project.

### Status Report

See PHP & Laravel version:

```php
php artisan about
```

### Documentation Guide

```php
php artisan docs
```

### All Commands

```php
php artisan list
```

### Interactive Shell

```php
php artisan tinker
```

### Clear Caches

```php
php artisan cache:clear
```

### Seed Database

```php
php artisan db:seed
```

### Create View Component

```php
php artisan make:component
```

### Create Controller

```php
php artisan make:controller
```

### Create Factory

```php
php artisan make:factory
```

### Create Migration

```php
php artisan make:migration
```

### Create Seeder

```php
php artisan make:seeder
```

### Create Model

Create eloquent models and accompanying files.

```php
php artisan make:model
```

```php
php artisan make:model -c /* Make accompanying controller */
```

```php
php artisan make:model -f /* Make accompanying factory */
```

```php
php artisan make:model -m /* Make accompanying model  */
```

```php
php artisan make:model -s /* Make accompanying seeder */
```