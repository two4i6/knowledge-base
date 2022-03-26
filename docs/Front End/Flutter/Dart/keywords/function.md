# Function
- Functions are objects.
	- The type if ```Function```
	- Can be assigned to variables
	- Can be passed to methods (for a callback) 

## Parameters
### Positional
```dart
getHttpUrl(String server, String path, [int port=80]) {
  // ...
}

getHttpUrl('example.com', '/index.html', 8080); 
getHttpUrl('example.com', '/index.html');      
```

note: The parameter wrapped by `[ ]` is a positional optional parameter.

### Named
```dart
getHttpUrl(String server, String path, {int port = 80, int numRetries = 3}) {
  // ...
}

getHttpUrl('example.com', '/index.html');
getHttpUrl('example.com', '/index.html', port: 8080);
getHttpUrl('example.com', '/index.html', port: 8080, numRetries: 5);
getHttpUrl('example.com', '/index.html', numRetries: 5, port: 8080);
getHttpUrl('example.com', '/index.html', numRetries: 5);
```

note: Named parameters make for easier-to-understand call sites, especially when there are boolean flags or out-of-context numbers.
