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

```
composer create-project laravel/laravel example-app
```

### Global:

```
composer global require laravel/installer
```

```
laravel new example-app
```

### Use DDEV to get the application running:

```
ddev config
```

```
ddev start
```