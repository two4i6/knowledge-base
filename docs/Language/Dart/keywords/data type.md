# Data Type
## dynamic

## String
- Initialized with single, double or triple quotes
- use `[ ]` operator to access a particular character of a string
- use `+` operator to connect string, but *StringBuffer* is preferred (same as java Strings are immutable).

```dart
String a = 'string 1';
String b = "string 2";
String c = '''SELECT name
			  FROM people
		   ''';

String d = 'and $a'; // and string 1
String e = a[0];     // s
```

## Boolean
- *true* and *false* are Boolean literals

```dart
bool test = 5 == 0; //false
bool opposite = !test; // true
bool falseVal = !true; // false
```

