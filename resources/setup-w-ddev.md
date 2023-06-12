# Setup with DDEV

## Requirements

- PHP
- Composer
- Docker Desktop
- DDEV
- *NPM - Optional, but recommended*
- *Node - Optional, but recommended*

## Setup

You can require Laravel on a per-project basis, or use a global installer.

### Per-project:

```php
composer create-project laravel/laravel example-app
```

### Global:

```php
composer global require laravel/installer
```

```php
laravel new example-app
```

### Use DDEV to get the application running:

```php
ddev config
```

```php
ddev start
```