---
{"dg-publish":true,"permalink":"/learning/code/laravel/notes/6-layouts/","tags":["blade"]}
---

<z# Laravel Templates

Templates in Laravel help us define a solid structure for our HTML. They help maintain the structure that repeats in several Blade files. An example of this (assuming the project requires it) is that every page must have a logo, a header with a navbar, and a footer. Having more or less this structure:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <link rel="shortcut icon" href="" />
    <title>Document</title>
</head>
<body>
    <header>
        <nav></nav>
    </header>
    <footer></footer>
</body>
</html>
```

This template will repeat in most of the project views.

## Component Templates

In `Components/welcome-layout.blade.php`:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <link rel="shortcut icon" href="" />
    <title>Document</title>
</head>
<body>
    <header>
        <x-navbar></x-navbar>
    </header>
    <!-- All content here -->
    {{ $slot }}
    <footer></footer>
</body>
</html>
```

In `Components/navbar.blade.php` we find the `navbar` component for the `welcome-layout.blade.php` template.

And in the root of `Views` we have, for example, `home.blade.php`:

```html
<x-welcome-layout>
    Hello World
</x-welcome-layout>
```

This is a more modern way to create templates, however, many projects still work with another type of templates, which we will see now.

## Layout Templates

We will create a `Layouts` folder inside `Views` and create our template inside it.

For example, we will create a new template in: `Layouts/main.blade.php`

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
    <title>Document</title>
</head>
<body>
    <header>
        <x-navbar></x-navbar>    
    </header>
    <br><br><br><br>
    <!-- All content here -->
    {{-- This structure changes --}}
    @yield('content')
    <footer></footer>
    <script src="{{ asset('../resources/js/script.js') }}"></script>
</body>
</html>
```

In the root page (example) `home.blade.php` we put the following:

```html
@extends('layouts.main')

@section('content')
    Here goes the HTML content
@endsection
```

It's also possible to add several `@section` and `@stack` elements. They are almost the same, but `@stack` is used to add variable content:

```html
@stack('css')
```

In my root page `home.blade.php` I would put something like:

```html
@push('css')
    <style>...</style>
@endpush
```

The difference is that `@yield` only has one content, and this cannot be added to (meaning that one `@yield` corresponds to one `@section`). It is defined in a **unique** way in the root page `home.blade.php`. While `@stack` can have additions thanks to the `@push` statement.

This means I can add CSS content to my `@stack('css')` several times.
