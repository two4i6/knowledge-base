## Generic methods
```dart
T printFirst<T>(List<T> lst){
	T first = lst[0];
	print(first);
	return first;
}
```

## Generic classes
```dart
class myClass<T,E extends num> {
	T t;
	E e;
	List<T> listT = <T>[];

	MyClass(this.t, this.e);
}

void main(){
	var myClass = MyClass<int, double>(8, 18);
}
```