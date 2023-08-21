# Collection
List, Set, Map, Queue...

## Spread operator
- Add the contents of a Collection to a surrounding collection.
- Can be paired with `?` null-awareness `...?collection`
	- Only adds the items if collection is not null.

```dart
var a = [4,5,6];
var b = {1,2,3, ...a}; // {1,2,3,4,5,6}
```

## List
- List is abstract, creating a List actually calls a factory method to create a List sub-type.
- 