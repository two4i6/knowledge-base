```js
function repeatStringNumTimes(str, num) {
	return num > 0 ? str + repeatStringNumTimes(str, num-1) : '';
}
```

```js
function repeatStringNumTimes(str, num) { 
	let accumulatedStr = ""; 
	for (let i = 0; i < num; i++) { 
		accumulatedStr += str; 
	} 
	return accumulatedStr; }
```