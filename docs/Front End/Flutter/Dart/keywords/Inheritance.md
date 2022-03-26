# Inheritance and Subclassing

## Extends
```dart
class Animal{
	final String name;
	Animal(this.name);
	void toString(){
		print(name);
	}
}

class Cat extends Animal{
	final String name;
	final String color;
	Cat(string name, String color) : this.name = name, super(name){
		// use super.method
	}
	
	// don't need override
	void toString(){
		print('$color cat: +' super.name);
	}
}

void main(){
	final animal = Cat('cc', 'black');
	animal.toString(); // black cat: cc
}
```

## Abstract classes
```dart
abstract class Animal{
	void update();
}

class cat implements Animal{
	@override
	void update(){
		...
	}
}

```

## Mixin
"cousin" of abstract classes.
- Class with **no constructor** that can be attached (or mixed) with another class.
- Use the `with` keyword to 'add' the mixin class to another class.
- Mixins can be constrained to only certain sub-classes using the `on` keyword.

## with
```dart
class myCounter{
	int _count = 0;
	int next() => ++_count;
}

class myOperation {
	void operate() => print("executing some");
}

class Mixin extends myOperation with myCounter {
	void operate() {
		super.operate();
		next();
		print("executed: $_count items");
	}
}

void main(){
	Mixin().operate();
}
```

## on
The `on` key word is like `extends`, it make a mixin only able to `with`  to the following class.

```dart
class myCounter{
	int _count = 0;
	int next() => ++_count;
}

mixin myOperation on Mixin {
	void operate() => print("executing some");
}

abstract class Mixin with myCounter{}

class test extends Mixin with myOperation {
  	void operate() {
		super.operate();
		next();
		print("executed: $_count items");
	}
}

void main(){
	test().operate();
}
```