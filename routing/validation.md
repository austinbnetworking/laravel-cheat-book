# Validation

[&larr; Home](../README.md)

Laravel provides several different approaches to validate our application's incoming data. It is most common to use the `validate` method available on all incoming HTTP requests.

GET requests are intended to retrieve data from a server and do not modify the server’s state. On the other hand, POST requests are used to send data to the server for processing and may modify the server’s state. The route of a form request should be post, defined in the routes file. 

Validation Documentation: [https://laravel.com/docs/10.x/validation](https://laravel.com/docs/10.x/validation)

Validation Rules: [https://laravel.com/docs/10.x/validation#available-validation-rules](https://laravel.com/docs/10.x/validation#available-validation-rules)

### Validate method

We can use the `validate` method provided by the `Illuminate\Http\Request` object to validate. If the validation rules pass, code will keep executing normally; however, if validation fails, an `Illuminate\Validation\ValidationException` exception will be thrown and the proper error response will automatically be sent back to the user.

```php
/**
 * Store a new blog post.
 */
public function store(Request $request): RedirectResponse
{
    $validated = $request->validate([
        'title' => 'required|unique:posts|max:255',
        'body' => 'required',
    ]);
 
    // The blog post is valid...
 
    return redirect('/posts');
}
```

### Displaying The Validation Errors

When validation fails, laravel will automatically send back all the request data, and in addition provide an `$errors` variable. This variable is available to all views. Remember, we are automatically redirected back to the previous page when validation fails.  

```php
@if ($errors->any())
    <div class="alert alert-danger">
        <ul>
            @foreach ($errors->all() as $error)
                <li>{{ $error }}</li>
            @endforeach
        </ul>
    </div>
@endif
```

Alternatively, we can use the `@error` blade directive. This directive checks **if** validation errors exist for a given attribute. If the error is present, we can then use the `$message` variable to output the error. 

```php
<label for="title">Post Title</label>
 
<input id="title"
    type="text"
    name="title"
    class="@error('title') is-invalid @enderror">
 
@error('title')
    <div class="alert alert-danger">{{ $message }}</div>
@enderror
```

***