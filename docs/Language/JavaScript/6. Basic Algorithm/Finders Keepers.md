# Finders Keepers
```js
function findElement(arr, func) {
	for (let i = 0; i < arr.length; i++){
		if(func(arr[i]))
			return arr[i];
	}
	return undefined;
}
```

```js
function findElement(arr, func) {
	let num = 0;
	return arr.length === 0 ? undefined : func(num = arr.shift()) ? num 
	: findElement(arr, func);
}
```

```js
function findElement(arr, func) {
	return arr[arr.map(func).indexOf(true)];
}
```