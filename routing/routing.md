# Routing

[&larr; Home](../README.md)

***

A route is a PHP class that provides all the functionality we need to map views and controllers to destinations. 

Documentation: [https://laravel.com/docs/10.x/routing](https://laravel.com/docs/10.x/routing)

## File Locations

- `/routes`
    - Common routes - `web.php`
    - Back-end API’s - `api.php`

## Routing
Basic Routing:
1. The route class provides methods for handling http requests:
    1. `Route::get`, `Route::post`, etc.
2. The route method expects an endpoint and an enclosure as parameters.
    1. The end point is the path.
    2. The enclosure is a function or callable.
    3. Routes can accept wildcards.
3. The route method expects a response object that can be displayed. 
    1. Basic string: `return 'Hello World';`
    2. Return a view: `return view('welcome');`
4. Routes provide debugging tools:
    1. Stop code and inspect variables: `dd()`
    2. View extensive debugging information: `ddd()`

Advanced Routing: 
1. Pass in the request object to receive request information, such as query parameters.
    1. `Route::get('/search', function(Request $request) {`
    2. Example:
        1. If the URL is: `‘/search?name=Austin&city=Des Moines’`
        2. Use: `$request->name` and `$request->city` to access those parameters.

## Full Example

File: `/routes/web.php`

```php
<?php

// All Listings
Route::get('/', function () {
    return view('listings', [
        'heading' => 'Latest Listings', // Pass data to the view
        'listings' => Listing::all()
    ]);
});

// Single Listing
Route::get('/listings/{id}', function ($id) { // Accept a wildcard
    return view('listing', [
        'listing' => Listing::find($id)
    ]);
});
```