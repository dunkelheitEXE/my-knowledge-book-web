---
{"dg-publish":true,"permalink":"/learning/code/laravel/notes/3-http-requests/"}
---

# HTTP Requests
- [[#What are they?|What are they?]]
- [[#Types of queries|Types of queries]]
	- [[#Types of queries#GET|GET]]
	- [[#Types of queries#POST|POST]]
		- [[#POST#POST|POST]]
		- [[#POST#PUT Y PATCH|PUT Y PATCH]]
		- [[#POST#DELETE|DELETE]]

---
## What are they?

- An HTTP request is a message sent by a client (such as a web browser) to a server to request a resource or perform an action.

## Types of queries

### GET

- They are queries that are executed in the URL:

```shell
http://alfred.com/hack?hack="123"
```

In this case, ``hack`` is the variable, and its value is ``123``

Also, this type of query is used to render parts of the webpage. To **get** all data and show it to the user

```php
Route::get("", function () {
	return "Hello world";
});
```

### POST

- There are three of this type. Actually, they are the same thing, but there are specific differences about functionality and when we must use one

#### POST

It is the most common, it is used when you send information through a form

```html
<form action="/send" method="POST">
	<input type="text" name="name">
	<input type="submit" value="Submit">
</form>
```

```php
Route::post("/create", function () {
	return "To create";
});
```

#### PUT Y PATCH

They are using to update records

**PUT**

- To update a whole record

```php
Route::put("/update", function () {
	return "To update";
});
```

**PATCH**

- To update partially a record

```php
Route::patch("/update-partial", function () {
	return "To update";
});
```

#### DELETE

- To delete a record

```php
Route::post("/delete", function () {
	return "To delete"
});
```

