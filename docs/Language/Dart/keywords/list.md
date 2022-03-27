# List 
- Dart only has generic containers (e.g ```List<T>```).
- No array type, array are intended as instances of ```List<T>```.

```dart
List<double> listOfDbls = new List<double>();
final myuList = [1,2,3];
```

Useful methods / attributes:
- .length
- .add(T value)
- .isEmpty
- .contains(T value)
- .forEach((e) => print(e))
- .iterator ```while(iter.moveNext()) print(iter.current)```