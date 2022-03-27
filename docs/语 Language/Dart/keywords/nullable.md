# Nullable

# Declare
```dart
class myClass{
	String? str;

	myClass(this.str);
}
```

# Operator
`?` used to declaration a type that may be null.
```dart
String? str;
print(str); // prints null
```

`?[]` used with index operation.
```dart
print(str[0]); // prints null
```

`!` convert a nullable into a non-nullable.
```dart
String nStr = str! // possible exception
```

`??` used to produce a non-nullable value from a nullable one
```dart
int? nullable;
int nonNullable = nullable ?? 0; //give 0
```

