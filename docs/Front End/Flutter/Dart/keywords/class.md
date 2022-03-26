# Class
```dart
class MyClass {

}
```

## Initializer
```dart
class MyClass {
	String str = 'hello';
	MyClass();

	// or
	MyClass() : str = 'world';
}
```

## Constructors
```dart
class MyClass {
	String? str; 
	// or
	late String str;

	// constructor	
	MyClass(String str) {
		this.str = str;
	}
	// or
	MyClass(this.str);
}
```

or 

```dart
class MyClass {
	String str;

	MyClass(String val) : a = val;
}
```

### Named Constructor
```dart
class MyClass {
	final str;
	
	MyClass(this.str);
  
	MyClass.named() : str = '';
}

void main() {
	MyClass myclass = MyClass.named();
}
```

## Factory Constructor
use keyword `factory` to denote a factory constructor. (doesn't always create a new instance)
- An instance of a subclass
- An singelton
- No access to this

```dart
class MyClass {
	late String str;
	MyClass(this.str);

	factory MyClass.createClass({required String str, bool isDone=false}){
		if(isDone){
			return MyClass('done');
		}
		return MyClass('not donw');
	}
}

void main{
	MyClass.createClass(str: 'hello');
}
```

### Singleton
```dart
class Singleton {
	// static
	static final Singleton _singleton = Singleton._internal();

	// private named contructor
	Singleton._internal();
	
	factory Singleton() {
		return _singleton;
	}
}

void main(){
	Singleton()
}
```
