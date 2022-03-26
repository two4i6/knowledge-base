# Object
```dart
class myClass{
	final String str;
	myClass(this.str);
	void toString(){
		print(str);
	}
}

void main(){
	final obj = myClass('hello');
	print(obj.toString()); // hello
}
```