# Clone
## deep copy
Use a deep copy to clone an object.
- can make nice use of the nullable and `??` operator to allow certain constructor parameters to be modified.
- Ensure the copyWith method has the exact same parameter list as the object constructor.

```dart
class myClass{
	final string _str;
	
	myClass(this._str);

	// deep copy
	myClass copyWith({String? str}) =>
		myClass(str ?? 'hello');
}
```

## shadow copy
If the class we want to clone contains an object or a collection.
Use shadow copy get the object reference to the field / objects contained within those objects.

```dart
class myClass2{
	myClass _mc;
	List<String> _listStr;

	//shadow copy
	myClass({required this._mc, required this._listStr})
}
```

## cloning primitive collections
```dart
listInts : listInts ?? []..addAll(this.listInts);

var str = ['a','b'];
var test = []..addAll(str);

//or 

var test = [...str];
```