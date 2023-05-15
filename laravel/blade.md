# Blade

Laravel uses a PHP templating engine called blade.

Blade Documentation: [https://laravel.com/docs/10.x/blade](https://laravel.com/docs/10.x/blade)

## Glossary

[Extending Templates](blade/extending-templates.md)

## File Locations

- Views - `/resources/views`

## Blade

- Echo: `{{ }}` `{{ $some_variable }}`
- Directives (Conditional Logic):  `@if()`, `@endif`, `@for()`, `@endfor`, `@php`, `@endphp`, etc.
- All Directives: [https://laravel.com/docs/10.x/blade#blade-directives](https://laravel.com/docs/10.x/blade#blade-directives)

## Blade Cook Book
Echo
```blade
{{ $name }}
```

Echo w/out escaping
```blade
{!! $name !!}
```

If Statement
```blade
@if ($some_validation)
    <!-- Some code.... -->
@elseif ($some_other_validation)
    <!-- Some other code.... -->
@else
    <!-- Default code.... -->
@endif
```
