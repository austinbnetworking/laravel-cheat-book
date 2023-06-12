# Components

Components and slots provide similar benefits to sections, layouts, and includes; however, some may find the mental model of components and slots easier to understand.

Documentation: [https://laravel.com/docs/10.x/blade#components](https://laravel.com/docs/10.x/blade#components)

There are two types of components that can be used: Anonymous & Class Based. 

The main difference is that class-based components have an accompanying class that can handle preprocessing of data. Anonymous components may also receive data through props, but class-based gives this kind of computing a specific location to live. (Valuable to OOP)

I recommend using anonymous for the majority of components. If a component desires logic that is specific to ONLY that component, then make a class.

### Anonymous Components

To define an anonymous component, all you need to do is place a blade file inside of the`resources/views/components` directory.

You can use artisan to create one:

```php
php artisan make:component alert --view
```

### Class-Based Components

Class-based components are automatically discovered within the `app/View/Components` directory and `resources/views/components` directory, so no further component registration is typically required.

You can use artisan to create one:

```php
php artisan make:component Alert
```

### Rendering Components

You can render a component for this file: `alert.blade.php` like so: 

```php
<x-alert/>
```

### Slots

Slots are used to pass additional content, often in the form of other components, to components. 

To achieve this, we must echo a variable named `$slot` which can be used to render additional content. 

```php
## /resources/views/components/nav.blade.php

<nav>
	<div>Title</div>
	{{ $slot }}
</nav>
```

In another file, we can inject content into that component.

```php

## /resources/views/components/nav-links.blade.php

<x-nav>
    <a href="#">Link 1</a>
		<a href="#">Link 2</a>
		<a href="#">Link 3</a>
</x-nav>
```

Those two files would render as:

```php
<nav>
	<div>Title</div>
  <a href="#">Link 1</a>
	<a href="#">Link 2</a>
	<a href="#">Link 3</a>
</nav>
```