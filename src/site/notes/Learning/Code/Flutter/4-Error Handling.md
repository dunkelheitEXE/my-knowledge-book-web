---
{"dg-publish":true,"permalink":"/learning/code/flutter/4-error-handling/"}
---

## What does it consist?

In dart, like other programming languages, you can handle errors to prevent broking the program. The instruction in charge of this: ``try-catch``

### Example

```dart
import "dart:io";
void main () {
	stdout.write("Enter a number");
	try {
		String? stNumber = stdin.readLineSync();
		int? number = int.parse(stNumber ?? "");
	} catch(e, s) {
		print("Error: $e");
	}
}
```

In this case, we have a keyboard input and we are going to convert from string to int. However, the user could input a string that is not a number and cause a crash. Because of this, we have had to set this ``handler``

>[!NOTE] Note
>#### Handler
>As its name says, it is in charge to manage and handle errors that break the program. There are many forms to handle them, we will see this later



