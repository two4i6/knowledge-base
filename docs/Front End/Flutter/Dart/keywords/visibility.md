# Visibility
- In dart everything is public by default.
- Prepend _ to a name (instance variable or method named) to make it private.

```dart
class MyClass {
	// private instance field
	String _name;

	MyClass(this._name);

	// private method
	void _printNumber(int a){
		var s = _name + "$a";
		print(s);
	}
}

// a class that isn't visible outside
class _hiddenClass{
}
```

