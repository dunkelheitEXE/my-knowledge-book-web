---
{"dg-publish":true,"permalink":"/learning/code/laravel/notes/5-components/","tags":["blade"]}
---

# Index
- [[#Anonymous Components|Anonymous Components]]
	- [[#Anonymous Components#Creation|Creation]]
	- [[#Anonymous Components#Call the component in a Blade view|Call the component in a Blade view]]
- [[#Values inside a component|Values inside a component]]
	- [[#Values inside a component#Named slot|Named slot]]
- [[#Component attributes|Component attributes]]
- [[#Adding parameters|Adding parameters]]
- [[#Class Components|Class Components]]

## Anonymous Components

### Creation

To create a component, we create our component inside a folder called `components`.

**For example: `alert.blade.php`**. Remember this file goes inside the `Components` folder.

```html
<div class="p-5 flex justify-center items-center bg-neutral-900 text-neutral-100">
		This is a tag
</div>
```

### Call the component in a Blade view

Inside our `.blade.php` view, we call components by using opening and closing HTML tags: `<></>`

Once we have the tags, we put the prefix `x-` inside them. After the dash, we put the name of the `.blade.php` file that has the component. In this example it would be `x-alert` like this:

```html
<body>
		<!-- Here is our component -->
		<x-alert></x-alert>
</body>
```

## Values inside a component

You can change the content of each component, even if you use it in many places. This is the **main goal** of components. They are like **templates** that you can use in many places.

This template feature lets components have different values or change them from the main view. Here is an example:

```html
<body>
		<x-alert>
				This is a value inside the component
		</x-alert>
</body>
```

In the component, you write this:

```html
<div class="p-5 flex justify-center items-center bg-neutral-900 text-neutral-100">
		{{ $slot }}
</div>
```

Here, the text _This is a value inside the component_ will show inside the Blade component where we put the `$slot` variable.

### Named slot

A named slot is like the default slot where we can put content, but with a specific name.

We use this because many times we want to use more than one variable content, like in this example:

File: `Components/component.blade.php`

```html
<!-- Component with two slots -->
<div class="p-5 flex justify-center items-center bg-neutral-900 text-neutral-100">
		<!-- Here the title content will show -->
		{{ $title }}
		<!-- Here the default content will show -->
		{{ $slot }}
</div>
```

In the view: `Views/View.blade.php`

```html
<body>
		<x-component>
				<x-slot name="title">Title</x-slot>
				This is the default content
		</x-component>
</body>
```

If you comment out the slot called `{{ $title }}` on either the `view` side or the `component` side, or if you don't define this variable in one of the two files (view or component), it will give an error.

To prevent this error and make any value optional in any component variable, you do this:

In: `Components/component.blade.php`

```html
<div class="...">
		<!-- Here we put ?? and then the title we want to show if nothing is put in that variable -->
		{{ $title ?? "Default title" }}
		...
</div>
```

## Component attributes

You can define attributes for a component. These attributes might seem useless at first, but they let you define even more variety for the component:

File: `Views/view.blade.php`

```html
<body>
		<!-- Here we define the 'type' variable 
		with the example value "success" -->
		<x-alert type="success">
				<x-slot name="title">
						Success
				</x-slot>
				Form sent successfully
		</x-alert>
</body>
```

Now, to receive this attribute in the component, you do it like this. In the file: `Components/alert.blade.php`

The component we will use as an example:

```html
<div class="flex justify-center items-center w-3/4 bg-neutral-100">
		<span class="font-semibold text-lg">{{ $title }}</span>
		{{ $slot }}
</div>
```

```html
<!-- We call a blade directive called "props" -->
@props(['type'])

<!-- Now that we received the 'type' variable, we create a piece of PHP code. In this case it's a 'switch' statement. Depending on what we receive in the 'type' variable, we change its color. For example, if the variable has 'success', as set above, its color will be green. Each type will have a color. -->

@php
		switch($type) {
				case 'success':
						$class="flex justify-center items-center w-3/4 bg-[#55bf7a] text-neutral-100";
						break;
				case 'danger':
						$class="flex justify-center items-center w-3/4 bg-[#bf5555] text-neutral-100";
						break;
				case 'info':
						$class="flex justify-center items-center w-3/4 bg-[#67abcd] text-neutral-100";
						break;
				case 'warning':
						...
						break;
				case 'dark':
						...
						break;
				default:
						//... In case it's none of them
						$class="flex justify-center items-center w-3/4 bg-neutral-100";
						break;
		}
@endphp

<div class={{ $class }}>
		...
</div>

```

If we want the `props` to have a default value, we simply define it like this:

In `Components/alert.blade.php`

```html
@props(['type' => 'info'])

...
```

## Adding parameters

If you want to add more parameters to a component, you do it like this:

Let's say the new parameter to add is a class (`class`), you do this:

In: `Views/example.blade.php`

```html
<body>
		<!-- We add the 'class' parameter -->
		<x-component type="success" class="mb-3">
				...
		</x-component>
</body>
```

If the `type` variable/parameter defines a specific class for `x-component`, then `class` is an addition to that existing class or the one defined by `type`. So we need to understand this:

In `Components/component.blade.php`

```html
@props(['type' => 'info'])

@php
...
@endphp

<div class="{{ $class }}">
		<span class="font-semibold text-lg">{{ $title }}</span>
		{{ $slot }}
</div>
```

First, notice that the `class` parameter is not received in the `@props`. If an attribute is not received in this Blade property, what happens is that it gets saved in a background variable called `$attributes`.

To properly add this class to our component's class, we need to "merge" the classes, and we do it like this:

```html
@props(['type' => 'info'])

@php
...
@endphp

<div class="" {{ $attributes->merge(['class' => $class]) }}>
		<span class="font-semibold text-lg">{{ $title }}</span>
		{{ $slot }}
</div>
```

This way we properly combine the existing classes or those defined within the `@props` (in this example, done this way) and the classes that come as extra parameters in the `$attributes` variable.

## Class Components

This way is the best for defining components and consists of first running the command:

```shell
php artisan make:component <component-name>
```

After that, it creates a class with the component name. In this case, both the file name and class name will be `<component-name>`. For this example, we'll call it `card`.

For standardization reasons, we change the first letter of the file created in `View/Components/card.php` to uppercase, so `Card.php`

The variables passed through the `@props` method will be passed through the class constructor function. ==All properties defined in the class can be accessed from the component view.==

```php
class Card extends Component
{
		public $class;

		public function __construct($type = 'info') {
				switch($type) {
						case 'success':
								$class="flex justify-center items-center w-3/4 bg-[#55bf7a] text-neutral-100";
								break;
						case 'danger':
								$class="flex justify-center items-center w-3/4 bg-[#bf5555] text-neutral-100";
								break;
						case 'info':
								$class="flex justify-center items-center w-3/4 bg-[#67abcd] text-neutral-100";
								break;
						case 'warning':
								$class="flex justify-center items-center w-3/4 bg-orange-500 text-neutral-100";
								break;
						case 'dark':
								$class="flex justify-center items-center w-3/4 bg-gray-200 text-neutral-800";
								break;
						default:
								//... In case it's none of them
								$class="flex justify-center items-center w-3/4 bg-neutral-100";
								break;
				}

				// Important to set the html property to the class property respectively
				$this->class = $class;
		}
}
```

This separates PHP logic from front-end logic. These types of components are called **class components**