---
{"dg-publish":true,"permalink":"/learning/code/flutter/first-program-in-flutter/"}
---

## Introduction

In flutter, al elements must be considered as widgets. Flutter app is made by widgets. A widget has a child content, this could be from a text to another widget

```dart
import 'package:flutter/material.dart';

void main() => runApp(NombreApp());

class NombreApp extends StatelessWidget {
  const NombreApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: "Mi primera app",
      home: Inicio()
    );
  }
}


class Inicio extends StatefulWidget {
  const Inicio({super.key});

  @override
  State<Inicio> createState() => _InicioState();
}

class _InicioState extends State<Inicio> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text("Mi primera App"),
      ),
      body: Center(
        child: Text("Hola Mundo"),
      ),
    );
  }
}
```

---
## Breaking down the code

### Classes and functions

**Main Function**: Function where your app will run

```dart
void main() {
	runApp(MyApp());
}
```

**StatelessWidget**: Class in charge to create the main widget (father)

```dart
class YourAppName extdends StatelessWidget {
	@override
	Widget build(BuildContext context) {
		return MaterialApp();
	}
}
```

This could be considered like a common/basic layout to Flutter app.

**Children**: Widga