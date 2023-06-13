# Environment

[&larr; Home](../README.md)

***

Laravel applications require a certain level of environment configurable settings to be applied. These settings could include items such as:

- Debug mode
- Database connection settings
- Mail host
- Private passwords, tokens, etc.  

They are meant to be ignored in repositories and configured at an environment level. They serve as one location of truth, and all locations needing to reference access only the label. 

For accessing these values, laravel has a helper function:

```php
env('SOME_VAR_TO_ACCESS', 'DEFAULT_VALUE_IF_NOT_EXISTENT')
```

For example, accessing the Database connection type would be like so:
```php
env('DB_CONNECTION', 'mysql')
```
