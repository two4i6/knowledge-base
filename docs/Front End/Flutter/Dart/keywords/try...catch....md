# try...catch...
```dart
try {

} on OutOfLlamasException {
	// a specific exception
} on Exception catch (e) {
	// anything else that is an exception
	print('Unknown exception: $e');
} catch (e) {
	// no specifed type, handles all
	print(e);
}
```

