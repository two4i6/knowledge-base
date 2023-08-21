# ENUM
- Use enumerated types to increase readability of code.
- Enums have an associated index value.
- Always fully qualify an enum to use it.

```dart
enum Fruits {
	apple,
	pear,
	grapes
}

var a = Fruites.apple.index; //0

Fruites best = Fruits.pear; 
bool = best == Fruits.pear; // true

print(Fruits.values); // [Fruits.apple, .., Fruits.grapes]

print(Fruits.values[0]); // Fruits.apple

print(Fruits.values[0].toString().split('.').last); //apple
```

