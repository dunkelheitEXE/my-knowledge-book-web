---
{"dg-publish":true,"permalink":"/learning/code/laravel/notes/4-models-and-controllers/"}
---

# Models & Controllers

## Create a model or controller

To create any type of file, you have to run: 

```powershell
php artisan make:<FileType> HomeType
```

For controllers:

```powershell
php artisan make:controller HomeController
```

### Controller Functions

When you create a controller, it has four functions that probably you will need in your whole application

```php
index()
show()

```

# Vistas.

## Mostrar Vistas

Para mostrar vistas en PHP Laravel, debemos ir al controlador y usar la línea `return view(”vista”)`.

```php
public function controller() {
		return view('dir.view')
}
```

## Vistas con parámetros.

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
