# Blade

Laravel uses a PHP templating engine called blade.

- [Laravel Blade Documentation](https://laravel.com/docs/10.x/blade)

## Glossary

- [Extending Templates W/ Yield](extending-templates-w-yield.md)

## File Locations

- Views - `/resources/views`

## Blade

- Echo: `{{ }}` `{{ $some_variable }}`
- Directives (Conditional Logic):  `@if()`, `@endif`, `@for()`, `@endfor`, `@php`, `@endphp`, etc.
- All Directives: [https://laravel.com/docs/10.x/blade#blade-directives](https://laravel.com/docs/10.x/blade#blade-directives)

## Blade Cheat Sheet
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
    <!-- Some code... -->
@else
    <!-- Default code... -->
@endif
```

For Loop
```blade
@for ($i = 0; $i < 10; $i++)
    <!-- Some code... -->
@endfor
 ```
 
For Each Loop
 ```blade
@foreach ($users as $user)
    <!-- Some code... -->
@endforeach
 ```
 
For Else Loop
 ```blade
@forelse ($users as $user)
    <!-- Some code... -->
@empty
    <!-- Some other code... -->
@endforelse
 ```
 
While Loop
 ```blade
@while (true)
    <!-- Some code... -->
@endwhile
```
