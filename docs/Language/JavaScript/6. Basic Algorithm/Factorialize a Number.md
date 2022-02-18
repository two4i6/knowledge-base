```js
function factorialize(num) {
	let result = 1;
	for(let i = 1; i <= num; i++){
		result *= i;
	}
	return result;
}
```

or 

```js
function factorialize(num) {
	if(num === 0)
		return 1;
	else
		return factorialize(num-1) * num;
}
```

or 

```js
function factorialize(num, factorial = 1) {
	if(num === 0)
		return factorial;
	else
		return factorialize(num - 1, factorial * num);
```

