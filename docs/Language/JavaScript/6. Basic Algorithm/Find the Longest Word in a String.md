```js
function findLongestWordLength(str) {
	return Math.max(...str.split(' ').map(x => x.length));
}
```

```js
function findLongestWordLength(str) { 
	let words = str.split(' '); 
	let maxLength = 0; 
	for (let i = 0; i < words.length; i++) { 
		if (words[i].length > maxLength) { 
			maxLength = words[i].length; 
		} 
	} 
return maxLength; 
}
```

```js
function findLongestWordLength(str) {
	const reducer = (x, y) => Math.max(x, y.length)
	return str.split(' ')
		.reduce(reducer, 0);
}
```