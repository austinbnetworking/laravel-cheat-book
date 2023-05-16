# Extending Templates W/ Yield

## Usage

In a base template, we can yield a location to be used when extending the template.

- The `@yield` directive takes a custom name parameter. This can be anything, often is a description of what the section is. 

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

In another file, we can extend the base template.

- The `@extends` directive takes a name parameter matching the file name of the base template. (`layout.blade.php` is `layout`)
- The `@section` directive takes a name parameter matching the section made with the `@yield` directive.

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
