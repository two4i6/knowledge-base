# Callbacks
![[Pasted image 20220324230559.png]]

```dart 
@override
Widget build(BuildContext context){
	return SomeWidget(
		MyListItem(myCallback);
	);
}

void myCallback(Item item){
	print('user tapped on $item');
}
```

