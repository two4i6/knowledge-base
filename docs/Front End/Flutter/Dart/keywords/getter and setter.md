# Getter and Setter
- Use `get` and `set` keyword.
- Behaves like a public variable at the calling site.
- Use getter and setter make the variable read-only or when there is some logic to setting the variable.

```dart
class myClass{
	int _num;

	myClass(this._num);
	
	int get num => _num;
	void set num(int num){
		_num = num;
	}
}
```
