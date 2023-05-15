# Routing

A route is a PHP class that provides all the functionality we need to map views and controllers to destinations. 

Documentation: [https://laravel.com/docs/10.x/routing](https://laravel.com/docs/10.x/routing)

## File Locations

- `/routes`
    - Common routes - `web.php`
    - Back-end API’s - `api.php`

## Routing

1. The route class provides methods for handling http requests:
    1. `Route::get(`
    2. `Route::post(`
2. The route method expects an endpoint and an enclosure as parameters.
    1. The end point is the path: `Route::get('/'`, `Route::get('/listings'`
    2. And the enclosure is a function: `Route::get('/', function () {`
    3. Add wildcards: `Route::get('/posts/{id}', function($id) {`
    4. Add constraints: `->where('id', '[0-9]+');`
3. The route method expects a response object that can be displayed. 
    1. Basic string: `return 'Hello World';`
    2. Return a view: `return view('welcome');`
    3. Return an object with custom response settings: 
        1. Achieved by using the `response()` container method
        2. Set the status code: `return response('<h1>Hello World</h1>', 200)`
        3. Set content type header: `->header('Content-Type', 'text/plain');`
        4. Set a custom header: `->header('foo', 'bar');`
4. The route method provides debugging tools:
    1. Stop code and inspect variables: `dd()`
    2. View extensive debugging information, such as the full request: `ddd()`
5. Pass in the request object to receive request information, such as query parameters.
    1. `Route::get('/search', function(Request $request) {`
    2. Example:
        1. If the URL is: `‘/search?name=Austin&city=Des Moines’`
        2. Use: `$request->name` and `$request->city` to access the parameters.

## Example

File: `/routes/web.php`

```php
<?php

use Illuminate\Http\Request;
use Illuminate\Support\Facades\Route;
use App\Models\Listing;

/*
|--------------------------------------------------------------------------
| Web Routes
|--------------------------------------------------------------------------
|
| Here is where you can register web routes for your application. These
| routes are loaded by the RouteServiceProvider within a group which
| contains the "web" middleware group. Now create something great!
|
*/

// All Listings
Route::get('/', function () {
    return view('listings', [
        'heading' => 'Latest Listings',
        'listings' => Listing::all()
    ]);
});

// Single Listing
Route::get('/listings/{id}', function ($id) {
    return view('listing', [
        'listing' => Listing::find($id)
    ]);
});
```