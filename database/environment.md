# Environment

[&larr; Home](../README.md)

***

Laravel applications require a certain level of environment configurable settings to be applied. 

These settings include items such as:

- Toggling debug mode
- Database connection settings
- Mail host provider
- Private passwords, tokens, etc.  

They are meant to be ignored in repositories and configured at an environment level. They serve as one location of truth. 

### Accessing configurations:

Use the `env()` function to access. 

```php
env('SOME_CONFIG', 'default')
```

For example:

```php
env('DB_CONNECTION', 'mysql')
```
