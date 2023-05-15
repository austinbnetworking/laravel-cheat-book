# Extending Templates using Yield

## Usage

Create a base template, and use the `@yield` directive to designate a place for dynamic code.

The `@yield` directive takes a custom name parameter. 

```blade
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Laragigs</title>
</head>

<body>
    <h1>Laragigs</h1>
    @yield('content')
</body>
</html>
```

To extend that code in another template, use the `@extends` & `@section` directives.

- The `@extends` directive accepts a name parameter matching the file name of the base template. (`layout.blade.php` is `layout`)
- The `@section` directive accepts a name parameter matching the section made with the `@yield` directive.

```blade
@extends('layout')

@section('content')
    
<h1>{{ $heading }}</h1>

@if(count($listings) == 0)
    <p>No listings found.</p>
@endif

@foreach ($listings as $listing)
    <h2><a href="/listings/{{ $listing['id'] }}">{{ $listing['title'] }}</a></h2>
    <p>{{ $listing['description'] }}</p>
@endforeach

@endsection
```
