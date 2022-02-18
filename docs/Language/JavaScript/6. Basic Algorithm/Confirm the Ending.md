```js
function confirmEnding(str, target) {
	return str.slice(str.length - target.length) === target;
}
```

```js
function confirmEnding(str, target) {
	let re = new RegExp(target + "$", "i"); 
	return re.test(str); 
}
```

```js
function confirmEnding(str, target) { 
	return str.slice(-target.length) === target 
}
```

```js
function confirmEnding(str, target) {
	return [...str].splice(str.length-target.length, target.length).join("") === target;
}
```