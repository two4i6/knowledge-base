```js
function largestOfFour(arr) {
	return [...arr.map(x => Math.max(...x))];
}
```

```js
function largestOfFour(arr) {
	return arr.map(group =>
				  group.reduce((prev, current) => 
							   current > prev ? current : prev) 
				  )
}
```

```js
function largestOfFour(arr, finalArr = []) {
	return !arr.length
		? finalArr
		: largestOfFour(arr.slice(1), finalArr.concat(Math.max(...arr[0])))
}
```