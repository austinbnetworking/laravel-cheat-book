# Setup with Valet

[&larr; Home](../README.md)

***

MacOS minimalist setup.

Valet Documentation: [https://laravel.com/docs/10.x/valet](https://laravel.com/docs/10.x/valet)

## Requirements

- PHP
- Composer
- MySQL 
  - SequelAce or some alternative
- Laravel Project
- Laravel Valet
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

### 2. Install Valet

First time installation requires a global install of valet:

```php
composer global require laravel/valet
```

```php
valet install
```

### 3. Setup Valet Serving Directory

Valet uses a single directory that will automatically know to serve all the applications in that folder. Set up a sites folder, and all immediate directories within will be valet servable by defualt. simply by accessing the `http://<directory-name>.test` url.

```php
cd ~/Sites
 
valet park
```

### 3a. Optionally, serve a single project outside the main serving directory

```php
valet link
```

Or serve at a specific url

```php 
valet link application // http://application.test
```

Valet also supports sub domains

```php
valet link api.application // http://api.application.test
```

