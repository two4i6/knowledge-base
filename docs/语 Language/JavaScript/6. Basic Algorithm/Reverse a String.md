# Reverse a String
```js
function reverseString(str) {
	let newStr = "";
	for(let i = str.length-1; i >= 0; i--){
	newStr += str[i];
	}
	return newStr;
}
```

or 

```js
function reverseString(str) {
	return [...str].reverse().join('');
}
```

