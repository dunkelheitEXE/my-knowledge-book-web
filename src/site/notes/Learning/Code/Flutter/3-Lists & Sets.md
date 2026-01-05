---
{"dg-publish":true,"permalink":"/learning/code/flutter/3-lists-and-sets/"}
---

# Content

- [[#Lists|Lists]]
	- [[#Lists#Replacement|Replacement]]
- [[#Functions|Functions]]
	- [[#Functions#Add Elements|Add Elements]]
		- [[#Add Elements#Insert Method|Insert Method]]
	- [[#Functions#Remove|Remove]]
		- [[#Remove#By element|By element]]
		- [[#Remove#By index|By index]]
		- [[#Remove#Remove all|Remove all]]
- [[#Sets|Sets]]
	- [[#Sets#Definition|Definition]]
	- [[#Sets#Example|Example]]
	- [[#Sets#Functions|Functions]]
		- [[#Functions#Add elements|Add elements]]
		- [[#Functions#Remove Elements|Remove Elements]]
		- [[#Functions#Clear "set" list|Clear "set" list]]
		- [[#Functions#Remove a bunch of elements|Remove a bunch of elements]]
		- [[#Functions#Get length|Get length]]
		- [[#Functions#Knowing if something exists|Knowing if something exists]]
- [[#Convert a List to set|Convert a List to set]]
- [[#Map lists|Map lists]]
	- [[#Map lists#Set new Values|Set new Values]]
	- [[#Map lists#Functions|Functions]]
		- [[#Functions#Add a bunch of elements|Add a bunch of elements]]
		- [[#Functions#Add one single element|Add one single element]]
		- [[#Functions#Accessing to keys and its values|Accessing to keys and its values]]
		- [[#Functions#Proving if there is something existing in a map list|Proving if there is something existing in a map list]]
		- [[#Functions#Other common functions|Other common functions]]
- [[#Bucles for applied in lists|Bucles for applied in lists]]
- [[#Bucles for applied in maps|Bucles for applied in maps]]
- [[#Bucles foreach applied in lists and maps|Bucles foreach applied in lists and maps]]
	- [[#Bucles foreach applied in lists and maps#Lists and sets|Lists and sets]]
	- [[#Bucles foreach applied in lists and maps#Maps|Maps]]

## Lists

Lists, as they name say, can list a lot of values, this values will be determinated by the type of data which is defined **after** the list definition, and it has to be between ``<>``.

```dart
List<TypeOfData> list1 = [];
```

### Replacement

You can replace values inside of a list, like other programming languages

```dart
List<String> lista = ["Jhon", "Marston"];
// We're going to replace "Jhon" by "Arthur" and "Marston" by "Morgan"
lista[0] = "Arthur";
lista[1] = "Morgan";
```

## Functions

In a list, you can add, delete, modify and read all data inside of a list
### Add Elements

You will be able to add element by element (individually) or a bunch of values. See the example below

```dart
List<String> list1 = ["Hi!"];
list1.add("I'm"); // An individual element

List<String> listToAdd = ["Alan", ":D"];
list1.addAll(listToAdd);
```

Also, you can add lists manually when you create a new list. You can do it using ``...`` before the name if the list to add. See the sample below:

```dart
List<int> list1 = [1,2,3];
List<int> list2 = [4,5,6];

List<int> completeList = [...list1, ...list2, 7, 8]; // Using "..."
```

#### Insert Method

This method allows you to insert an element in an specific index inside of the list:

```dart
// First Parameter is the index desired to insert the element, that is the second parameter
completeList.insert(1, 2)
```

### Remove

#### By element

You can remove values from a list using the method ``remove``:

```dart
// A bunch of code here :D
list.remove("bannana");
// ...
```

This method returns ``true`` if something inside has been removed, or ``false`` otherwise.

```dart
bool removed = list.remove("bannana2");
```

#### By index

As its name says, This method will remove the element of the index specified as parameter

```Dart
list.removeAt(2);
```

This method return the element in that index:

```dart
int numberInTheList = list.removeAt(2);
```

#### Remove all

To clear all list, you have tu use:

```dart
list.clear();
```

## Sets

### Definition

>[!QUOTE] What Are sets in Flutter?
>In Flutter (usingDart), sets are unordered collections of unique elements. Unlike lists, they do not allow duplicate values and do not maintain the order in which elements were added. Sets are useful for ensuring uniqueness, removing duplicates from a list, and performing mathematical set operations like union and intersection

### Example

```dart
// Set<DataType> = [data]
Set<String> name = {"Alan", "dunkel"};
```

### Functions

#### Add elements

As a "set" list, it is not allowed duplicating elements, Flutter directly will skip this attemp to add something existing in the list. For example, following the previous example (using name list), "Alan" already exists, so if I try to add "Alan" twice, you can see what will happen below

```dart
name.add("Alan");
print(name);
```

Output

```bash
{"Alan", "dunkel"}
```

>[!NOTE]
>It is importante to say that if there is a word begining with Capital letter (for example, Jhon) and you add the same word (jhon) but begining with lower case, Those will be able to coexist
>
>```dart
>name.add("alan");
>```
>
>**Output will be**:
>
>```shell
>{"Alan", "dunkel", "alan"}
>```

#### Remove Elements

To remove elements, `.remove()` is the functions that does this. Taking the last case as example:

```dart
name.remove("alan");
print(name);
```

Output:

```shell
{"Alan", "dunkel"}
```

#### Clear "set" list

```dart
name.clear()
```

#### Remove a bunch of elements

```dart
Set<String> name2 = {"Alan", "dunkel"};
name.removeAll(name2); // This removes all elements inside of 'name2'
```

#### Get length

```dart
int nameAmount = name.length;
```

#### Knowing if something exists

In dart, in "set" lists section, you will find `contains()` method, thata returns bool proving if something exists or not:

```dart
name.contains("Alan"); // this returns true
name.contains("alan"); // this returns false
```

## Convert a List to set

It is useful if you want to delete elements repeated, because when you convert a list to "set" list, elements repeated are automatically eliminated

```dart
List<String> list = ["One", "two", "One"];
Set<String> newList = Set.from(list);
```

## Map lists

In other programming languages, to this type of lists are known like "dictionaries". You have a **key**, and each key has a **value**

```dart
Map<String, String> users = {
	"Admin": "Alan",
	"User": "Alfonso",
	"Customer": "Job"
};
```

Also key may have different data type from its value:

```dart
Map<String, float> accounts = {
	"alan223hfr": 200.0,
	"alfonxxsw": 344.34,
	"jonsjob": 0.0
};
```

### Set new Values

If you want to change the amount of "alan", you have to access to the key of that value:

```dart
accounts["alan223hfr"] = 100.0;
```

### Functions

#### Add a bunch of elements

As you can in lists or "set" lists, you may add more elements:

```dart
Map<String, float> accountsAdded = {"alan22": 230.0, "josue": 1200.0};
accounts.addAll(accountsAdded);
```

#### Add one single element

Different from lists or "set" lists, here you only have to write a new key and its value:

```dart
accounts["alan333": 50.50]; // This does not exist in accounts, so it will be added inmediatly
```

#### Accessing to keys and its values

- `accounts.keys`: This will return all keys in `accounts`.
- `accounts.values`: This will return all values in `accounts`, without their keys.

#### Proving if there is something existing in a map list

If you want to know the existence of an specific element:

```dart
accounts.containsKey("key") // this will verify if "key" is inside of accounts as key value

accounts.containsValue("Value") // this will verify if "value" is inside of accounts as value
```

#### Other common functions

- `.clear()`: deletes all inside if a map list
- `.length`: This returns the length of a map list

## Bucles for applied in lists

We have two ways to pass through a list:

```dart
List<int> lista = [1,2,3,4];
for(var i = 0; i < lista.length; i++) {
	print("${lista[i]}")
}
```

or a kind of `foreach` function

```dart
for (int number in lista) {
	print("$number");
}
```

## Bucles for applied in maps

```dart
Map<int,int> listb = {1 => 100, 2 => 200, 3 => 300, 4 => 400};

for (var element in listb.entries) {
	print("${element.key} its value is ${element.value}");
}
```

## Bucles foreach applied in lists and maps

### Lists and sets

Foreach is a better way to pass through a list or map. For example:

```dart
Set<int> listc = {1,2,3,4};

listc.foreach(print)
```

This is the most efficient way to use it, but alse you can do this:

```dart
listc.foreach((item){
	print("$item");
});
```

### Maps

```dart
Map<String, float> accounts = {
	"111": 120.0,
	"222": 120.22,
	"333": 90.23
};

accounts.foreach((key, value){
	print("Key: $key; Value: $value");
});
```