# Operator Overloading
-   Arithmetic: +, -, *, /
-   Relational: >, <, <=, >=
-   Equality: !=, ==
-   ... many more

```dart
class myClass(){
	final String str;
	myClass(this.str);

	@override
	myClass operator +(myClass other){
		return myClass(other.str + str);
	}

	@override 
	bool operator ==(covariant myClass other){
		return other.str == str;
	}
	
	@override
	int get hashcode => name.hashcode;
}
```