# late
Using `late` when we don't want to initialize a variable immediately.
- E.g class instance fields.
- Verified at runtime.
- `late` defers initialization but still prohibits us from treating it like a nullable variable.

```dart
class Coffee {
	late final String _tem; // private variable
	
	void heat(){
		_tem = 'hot';
	}
	
	void chill(){
		_tem = 'iced';
	}

	String serve() => _tem + ' coffee';
}
```

The `final` allows `_tmp` to be immutable but assigned using one of `heat` or `chill` before it is used.

