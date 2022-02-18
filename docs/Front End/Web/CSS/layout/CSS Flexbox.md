# [[CSS Flexbox]]
Flexbox is powerful, well-supported layout method that was introduced with the latest version of CSS, CSS3. With flexbox, it's easy to center elements on the page and create dynamic user interfaces that shrink and expand automatically.

# Flex to Position Two Box
By placing the CSS property ```display: flex;``` on element allows us to use other flex properties to build a responsive page. For example:
```
.box {
	display: flex;
}
```
![[Pasted image 20220102154514.png]]
![[Pasted image 20220102154503.png]]

# Flex-direction 
Adding ```display: flex``` to an element turns it into a flex container. This make it possible to align any children of that element into rows or columns. We do this by adding the ```flex direction``` property to the parent item and setting it to ```row``` or ```column```. Creating a row will align the children horizontally, and creating a column will align the children vertically.

Other options for ```flex-direction``` are ```row-reverse``` and ```cloumn-reverse```. The default value for the ```flex-direction``` property is ```row```.

For example:
``` CSS
.box {
	dispaly: flex;
	flex-drection: cloumn;
}
```
![[Pasted image 20220102155706.png]]

# Justify-content 
Sometimes the flex items within a flex container do not fill all the space in the container. It is common to want to tell CSS how to align and space out the flex items a certain way. Fortunately, the ```justify-content``` property has several options to do this. 

Recall that setting a flex container as a row places the flex items side-by-side from left-to-right. A flex container set as a column places the flex items in a vertical stack from top-to-bottom. For each, the direction the flex items are arranged is called the **main axis**. For a row, this is a horizontal line that cuts through each item. And for a column, the main axis is vertical line through the items.

There are serval option for how to space the flex items along the line that is the **main axis**. 
![[Pasted image 20220102160601.png]]

- ```justify-content: center;```. which aligns all the flex items to the center inside the flex container.
![[Pasted image 20220102160538.png]]

- ```flex-start```: aligns item to the start pf the flex container.
![[Pasted image 20220102160631.png]]

- ```flex-end``` aligns items to the end of the flex container.
![[Pasted image 20220102160716.png]]

- ```space-between``` aligns items to the center of the main axis, with extra space placed between the items. The first and last items are pushed to the very edge of the flex container.
![[Pasted image 20220102160927.png]]

- ```space-around``` similar to ```space-between``` but the first and last item are not locked to the edges of the container, the space is distributed around all the items with a half space on either end of the flex container.
![[Pasted image 20220102161055.png]]

- ```space-evenly``` Distributes space evenly between the flex items with a full space at either end of the flex container
![[Pasted image 20220102161208.png]]


# Align items
The ```align-items``` property is similar to ```justify-content```. Flex container also have a **cross axis** which is the opposite of the main axis. For rows, the cross axis is vertical and for columns, the cross axis is horizontal.

CSS offers the ```align-items``` property to align flex items along the cross axis. For a row, it tells CSS how to push the items in the entire row up or down within the container, And for a column, how to push all the items left or right within the container.

![[Pasted image 20220102162147.png]]

The different values available for ```align-items``` include:
- ```center``` align items to the center.
![[Pasted image 20220102162240.png]]

- ```flex-start``` align items to the start of the flex container.
![[Pasted image 20220102162254.png]]

- ```flex-end``` align items to the end of flex container.
![[Pasted image 20220102162308.png]]

- ```stretch``` stretch the items to fill the flex container.
![[Pasted image 20220102162520.png]]

- ```baseline``` align items to their baselines. Baseline is a text concept, think of it as the line that the letters sit on.
![[Pasted image 20220102162547.png]]


# Flex wrap
By default, a flex container will fit all flex items together (a row will all be on one line). However, using the ```flex-wrap``` property tells CSS to wrap items. This means items move into a new row or column. The break point of where the wrapping happens depends on the size of the items and the size of the container.

There are 3 options for the direction of the wrap:
- ```nowrap```: this is the default setting, and does not wrap items.
![[Pasted image 20220102163616.png]]

- ```wrap```: wraps items onto multiple lines from top-to-bottom if they are in rows and left-to-right if they are in columns.
![[Pasted image 20220102163603.png]]

- ```wrap-reverse```: wrap items onto multiple lines from bottom-to-top if they are in rows and right-to-left if they are in columns.
![[Pasted image 20220102163639.png]]


# Flex shrink
When use the ```flex-shrink``` property, it allows an item to shrink if the flex container is too small. Items shrink when the width of the parent container is smaller than the combined widths of all the flex items within it.

The ```flex-shrink``` property takes number as values. The higher the number, the more it will shrink compared to the other items in the container. For example, if one item has a ```flex-shrink``` value of 1 and the other has a ```flex-shrink``` value of 3, the one with the value of 3 will shrink three times as much as the other.

For example:
![[Pasted image 20220102164109.png]]
``` CSS
#box-1 {
	background-color: dodgerblue;
	width: 100%;
	height: 200px;
	flex-shrink: 1;
}

#box-2 {
	background-color: orangered;
	width: 100%;
	height: 200px;
	flex-shrink: 2;
}
```
![[Pasted image 20220102164153.png]]


# Flex grow
The ```flex-grow``` is the opposite of ```flex-shirk```. The ```flex-shrink``` controls the size of the items when the container shrinks. The ```flex-grow``` property controls the size of items when the parent container expands.

 If one item has a `flex-grow` value of `1` and the other has a `flex-grow` value of `3`, the one with the value of `3` will grow three times as much as the other.

 For example:
``` CSS
#box-1 {
	background-color: dodgerblue;
	height: 200px;
	flex-grow: 1;
}

#box-2 {
	background-color: orangered;
	height: 200px;
	flex-grow: 2;
}
```
![[Pasted image 20220102164755.png]]


# Flex basis
The ```flex-basis``` property specifies the initial size of the item before CSS makes adjustment with ```flex-shrink``` or ```flex-grow```.

The units used by the ```flex-basis``` property are the same as other size properties (```px```, ```em```, ```%```, etc.). The value ```auto``` sizes items based on the content. 

For example: 
```CSS
#box-1 {
	background-color: dodgerblue;
	height: 200px;
	flex-basis: 10em;
}

#box-2 {
	background-color: orangered;
	height: 200px;
	flex-basis: 20em;
}
```
![[Pasted image 20220102170610.png]]


# Flex Shorthand
There is a shorthand available to set several flex properties at once. The ```flex-grow```, ```flex-shrink```, and ```flex-basis``` properties can all be together by using the ```flex``` property.

For example, ```flex: 1 0 10px;``` will set the item to ```flex-grow: 1```, ```flex-shrink:0```, and ```flex-basis: 10px```.

The default property setting are ```flex: 0 1 auto```.

For example: 
``` CSS
#box-1 {
	background-color: dodgerblue;
	flex: 2 2 150px;
	height: 200px;
}

#box-2 {
	background-color: orangered;
	flex: 1 1 150px;
	height: 200px;
}
```

# Rearrange Items
The ```order``` property is used to tell CSS the order of how flex items appear in the flex container. By default, items will appear in the sam order they come in the source HTML. The property takes numbers as values, and negative numbers can be used.

![[Pasted image 20220102171416.png]]
For example:
``` CSS
#box-1 {
	background-color: dodgerblue;
	order: 2;
	height: 200px;
	width: 200px;
}  

#box-2 {
	background-color: orangered;
	order: 1;
	height: 200px;
	width: 200px;
}
```
![[Pasted image 20220102171447.png]]


# Align self
The ```align-self``` property allow us to adjust each item's alignment individually, instead of setting them all at once. This is useful since other common adjustment techniques using the CSS properties `float`, `clear`, and `vertical-align` do not work on flex items.

```align-self``` accepts the same values as ```align-items``` and will override any value set by the ```align-items``` property.

For example:
``` CSS
#box-1 {
	background-color: dodgerblue;
	align-self: center;
	height: 200px;
	width: 200px;
}

  

#box-2 {
	background-color: orangered;
	align-self: flex-end;
	height: 200px;
	width: 200px;
}
```
![[Pasted image 20220102173022.png]]