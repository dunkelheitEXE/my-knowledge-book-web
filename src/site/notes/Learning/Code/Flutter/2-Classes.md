---
{"dg-publish":true,"permalink":"/learning/code/flutter/2-classes/"}
---

## Classes

```dart
void main () {
	// Creación de un objeto
	var ana = Persona("Ana", 30);
	ana.hablar(); // Llama al método hablar
}

class Persona {
  String nombre;
  int edad;

  // Constructor
  Persona(this.nombre, this.edad);

  // Método
  void hablar() {
	print("Hola, me llamo $nombre");
  }
}
```

Dart is an **Object Oriented Programming** Language, so, in this you must use many classes and methods

### Get methods

To code a *get* method:

```dart
class Product {
	int amount
	
	Product(this.amount);
	
	int get amount {
		return $amount;
	}
}
```

If you want to get in string format:

```dart
class Product {
	int amount
	
	Product(this.amount);
	
	String get amount {
		return "$amount"; // This could be between simple or double quation marks
	}
}
```

## Static Methods

```dart
class Example {
	static void staticMethodDoesSomething() {
		print("Static Method here!");
	}
}

void main() {
	Example.staticMethodDoesSomething();
}
```