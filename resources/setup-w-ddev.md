# Setup with DDEV

[&larr; Home](../README.md)

***

## Requirements

- PHP
- Composer
- Docker Desktop
- DDEV
- *NPM - Optional, but recommended*
- *Node - Optional, but recommended*

## Setup

You can require Laravel on a per-project basis, or use a global installer.

### 1. Install Laravel:

Using the per-project composer package:

```php
composer create-project laravel/laravel example-app
```

Using the global installer:

```php
composer global require laravel/installer
```

```php
laravel new example-app
```

### 2. Initialize DDEV Project:

```php
ddev config
```

### 3. Start Project:

```php
ddev start
```