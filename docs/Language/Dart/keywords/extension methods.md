# Extension methods
https://dart.dev/guides/language/extension-methods

```dart
class myClass{
	String str = 'hello';
}

extension printStr on myClass{
	void showStr(){
		print(str);
	}
}

// use a extension method
import 'Path of myClass' 
void main(){
	myClass obj = myClass();
	obj.showStr(); // hello
}

```

### Generic extension
```dart
extension MyFancyList<T> on List<T> { 
	int get doubleLength => length * 2; 
	List<T> operator -() => reversed.toList(); 
	List<List<T>> split(int at) => [sublist(0, at), sublist(at)]; 
}
```