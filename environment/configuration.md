# Configuration

[&larr; Home](../README.md)

***

Laravel offers application level configuration through the use of an ENV file.  

## Cache Configuration

### Clear Configuration Cache  

```php
php artisan config:clear
```

### Create Configuration Cache  

```php
php artisan config:cache
``` 
- Creates a cached file with all of the configuration options compiled into one file. When this is ran, the application will no longer read from the .env file, and instead reads from the cached file. This is only recommended to be ran in production, and is said to give an application a speed boost. If used, env variables should only be defined within configuration files, and nowhere else.  