---
{"dg-publish":true,"permalink":"/learning/code/flutter/chapter-1-introduction-to-dart/","tags":["Dart"]}
---

## Create a project

### A dart project

```shell
dart create my_project
```

### A Flutter Project

```shell
flutter create my_app
```

## Variables

In dart, there are two types of variables with a type of data: Variables that could be null and other must be something:

```dart
String name = "Alan" // this type NEEDS to have something, it cannot be null

String? secondName; // this type CAN be null
```

Also, all variables need to be **typed**

>[!QUOTE] Typed
>In programming context, it is a variable which needs to be related with a data type or this one has a data type which has been set, for example:
>- int or Integer
>- String
>- Boolean
>
>A data type determinates how a variable will work
