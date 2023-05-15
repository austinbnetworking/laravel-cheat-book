# Blade

Laravel uses a PHP templating engine called blade.

Blade Documentation: [https://laravel.com/docs/10.x/blade](https://laravel.com/docs/10.x/blade)

## Glossary

[Extending Templates](blade/extending-templates.md)

## File Locations

- Views - `/resources/views`

## Blade

- Print: `{{ }}`
- Print a variable: `{{ $some_variable }}`
- Directives (Conditional Logic):  `@if()`, `@endif`, `@for()`, `@endfor`, `@php`, `@endphp`, etc.
- All Directives: [https://laravel.com/docs/10.x/blade#blade-directives](https://laravel.com/docs/10.x/blade#blade-directives)

## Example

File: `/resources/views/listings.blade.php`

```blade
<h1>{{ $heading }}</h1>

@if(count($listings) == 0)
<p>No listings found.</p>
@endif

@foreach ($listings as $listing)
<h2><a href="/listings/{{ $listing['id'] }}">{{ $listing['title'] }}</a></h2>
<p>{{ $listing['description'] }}</p>
@endforeach
```
