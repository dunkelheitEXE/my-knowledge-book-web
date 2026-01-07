---
{"dg-publish":true,"permalink":"/chapter-5-views/","tags":["Laravel"]}
---

## What are the views?

Views are one of the most important and repetitive elements in Laravel. Here, HTML content and blade instructions will be.

Inside of the directory called `resources/views` we will be able to create our own views, and you will find the `welcome-view` that comes by default

### Building a view

The principles to build a view can be put into practice in `routes/web.php`

>[!INFO] What is web.php?
>This is the main file of our application paths. Here we will define where will be our routes and which [[HTTP Requests\|HTTP method]] we will use in each one.

Let's see an example of this. Here we defined a path for `root`, generally the `root` path is the welcome page or the home page of our application. So, when we start the server, the first thing that we will see is "Hello world":

```php
//in web.php
Route::get('/', function() {
	return "Hello World";
});
```

**Result:**

![Pasted image 20260106184124.png](/img/user/Pasted%20image%2020260106184124.png)

In this case the example is using a  GET method, and it returned a `Hello World`.

#### Building a view using controllers

Also, when  we build controllers, is important to understand that probably we use those controllers to manage data and show that data in a view. So, we are going to see the steps to follow to show a `Hello world` message. In this case we are going to use only `index` method.

1. We build the controller

```shell
php artisan make:controller RootController
```

2. We define the index method in the controller

```php
<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;

class RootController extends Controller
{
    //
    public function __invoke()
    {
        return "Hello from RootController";
    }

    public function index()
    {
        return "Hello from RootController using index method";
    }
}
```

3. We put it into `web.php`

```php
Route::get('/', [RootController::class, "index"]);
```

**Result:**

![Pasted image 20260106185301.png](/img/user/Pasted%20image%2020260106185301.png)

#### What is `__invoke()` method?

This method practically is a kind of `index` method that saves us time. We do not need to write an index method, so we directly can use it as a kind of `index`:

```php
<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;

class RootController extends Controller
{
    // We just let __invoke method
    public function __invoke()
    {
        return "Hello from RootController";
    }

    // We delete index from here ...
}
```

2. Now we call it in `web.php` *(Note that in this case we delete the `[]` that are around of the call of the controller)*:

```php
Route::get('/', RootController::class);
```

**Result:**

![Pasted image 20260106185941.png](/img/user/Pasted%20image%2020260106185941.png)

### Returned Views

Now, we are going to call views instead of just putting into `""` the word that we want to see. First we will go to `resources/views` inside of our project in the code editor of our preference and we are going to create a view, in this case is called `test-view.blade.php` and you can write something into the file:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
    <style>
        h1 {
            font-weight: 900;
            font-family: Arial, Helvetica, sans-serif;
            color:red;
        }
    </style>
    <h1>Hello world</h1>
</body>
</html>
```

Now, inside of `web.php` we can make a function that returns this:

```php
Route::get('/', function () {
    return view('test-view');
});
```

**The result will be the next:**

![Pasted image 20260106190842.png](/img/user/Pasted%20image%2020260106190842.png)

Using a controller is the same process, we only have to change `function(){}` by `ControllerName::class` and modify our controller (in this example called `RootController`):

```php
<?php
namespace App\Http\Controllers;

use Illuminate\Http\Request;

class RootController extends Controller
{
    //
    public function __invoke()
    {
        return view('test-view');
    }
}
```

```php
Route::get('/', RootController::class);
```

>[!INFO] Note
>If you are using an specific method in your controller, you only have to specify the method and put both into `[]`. It is something like this:
>
>```php
>Route::get('/', ControllerName::class); // ❌
>Route::get('/', [ControllerName::class, 'methodToShowView']); // ✅
>```

## Parameters in views

There are some ways to do that, one is passing by an `array` this parameters, the second one is using the function `compact()` or methods like `with()`. Let's see what to do in each one.

### Using only view()

```php
public function show($param) {
	return view('home-view', ["articleName"=>$param]);
}

public function show($articles) {
	// '$articles' is ["a1", "a2", "a3"]
	return view('list-view', ["articlesList"=>$articles])
}
```

### Using with()

```php
public function show() {
	return view('configuration')->with()
}
```

```php
public function home($param) {
	return view('home.index', compact($param))
}
```

Para mostrar estos parámetros, recordemos que en el archivo web debemos pasar los parámetros por la url:

```php
Route::get('usuarios/{user?}', [Controller::class, 'home']);
```

Y posteriormente mostrarlo en la vista. Por ejemplo: `Vista.blade.php`

```php
<h1>{{$param}}</h1
```



>[!QUOTE] **References**