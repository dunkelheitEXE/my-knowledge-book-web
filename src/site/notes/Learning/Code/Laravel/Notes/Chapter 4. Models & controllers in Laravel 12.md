---
{"dg-publish":true,"permalink":"/learning/code/laravel/notes/chapter-4-models-and-controllers-in-laravel-12/","tags":["Laravel"]}
---

# Models & Controllers

## Create a model or controller

To start, we have to create our Models and controllers. In Laravel 12, **Models** are PHP files that help us to manage the [[ORM (Object Relational Mapping)\|ORM (Object Relational Mapping)]], interacting directly with Databases.

### Models

Generating a Model is so easy, you just have to execute an `php artisan` command:

```shell
php artisan make:model User
```

For controllers:

```shell
php artisan make:controller UserController
```

>[!INFO] Tip
>Is recommended that you follow an specific syntax because many components in Laravel 12 works better based on elements like Models and ORM if you write correctly the syntax. *For example, you should write HomeController instead of just Home or ControllerHome*

### Controller Functions

When you create a controller, it should have some of the next (or all) methods. We are going to see these later.

```php
__invoke()
index()
show()
create()
store()
update()
edit()
```

