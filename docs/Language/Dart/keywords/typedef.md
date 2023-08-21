# typedef
- `typedef` allows one type to be specified by another name. In the other word, custom type.
	- since functions are types they can be `typedef`'d
- `typedef` long declarations for readability.
- leave Function types fully written out to aid clarity.

```dart
typedef LoggerFunc = void Function(String msg);
typedef ListMapper<X> = Map<X, List<X>>;

void printIntegers(LoggerFunc logger){
	logger("test");
}

void main() {
	printIntegers(print);
	ListMapper<String> m = {};
}
```

