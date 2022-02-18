# Visual Balance

# Position 
CSS trade each HTML element as its own box, which is usually referred to as the CSS Box Model. Block-level items automatically start on new line (heading, paragraphs, and divs) while inline item sit within surrounding content(images or spans). 

The default layout of elements in this way is called the normal flow of a document, but CSS offers the ```position``` property to override it.

## Relative Postion
When the position of an element is set to ```relative```, it allows us to specify how CSS should move it relative to its current position in the normal flow of the page. It pair with the CSS offset properties of ```left``` or ```right``` and ```top``` or ```bottom```. These say how many pixels, percentages, or ```em```s to move the item away from where it is normally positioned. For example:

``` CSS
p {
	position: relative;
	bottom: 10px;
}
```
This example moves the paragraph 10 pixels away from the bottom.
*Note: move an element's position to relative does not remove it from the normal flow, so other element around it still behave as if that item were in its default position.

## Absolute Position
The ```absolute``` will lock the element in place relative to its parent container. Unlike the ```relative``` position, this removes the element from the normal flow of the document, so surrounding items ignore it.  It pair with the CSS offset properties of ```left``` or ```right``` and ```top``` or ```bottom``` to adjust the position.  For example:

``` CSS
.box {
	position: absolute;
	top: 50px;
}
```

## Fixed Position
The ```fixed``` layout scheme is a type of absolute positioning that locks an element relative to the browser windows. Similar to absolute positioning, it's used with the CSS offset properties and also removes the element from the normal flow of the document. Other items no longer "realize" where it is positioned. 

One key different between ```absolute``` and ```fixed``` position is that an element with a fixed position won't move when the user scrolls. This look like:

``` CSS
.NavBar {
	position: fixed;
	top: 0px;
	left: 0px;
}

```

## Float Property
To push elements left or right, we can set ```float``` property of an element. Floating elements are removed from the normal flow of a document and pushed to either the ```left``` or ```right``` of their containing parent element. 

It's commonly used with the ```width``` property to specify how much horizontal space the floated element requires. For example:

``` CSS
.Left {
	float: left;
	width: 50%;
}

.right {
	float: right;
	width: 40%;
}
```
![[Pasted image 20211231220149.png]]




# Z-index
When elements are positioned to overlap. To change the position of overlapping element, we can use ```z-index``` property. It can specify the order of how elements are stacked on the top of one another. It must be integer, a higher value for the ```z-index``` property of an element move it higher in the stack than those with lower value. For example:

``` CSS
.box-a {
	z-index: 1;
}

.box-b {
	z-index: 2;
}
```
Here the ```box-b``` will be above of the ```box-a```.


# Size
## Width Property
 We can specify the width of an element using the ```width``` property in CSS. Value can be given in relative length units, such as ```em```; or absolute length unit, such as 
 ```px```; or as a percentage of its containing parent element. For example:

```css
img {
	width: 200px;
}
```

## Height Property
We can specify the height of an element using the ```height``` property in CSS. It is similar to the ```width``` property. For example:

```css
img {
	height: 20px;
}
```

## Transform Scale
To change the scale of an element, CSS has the ```transform``` property, along with its ```scale()``` function. For example:
``` CSS
p {
	transform: scale(2);
}
```

## Transform Skew
To skews the selected element along its X(horizontal) axis by a given degree by ```skewX()``` function from ```transform``` property. For example:
``` CSS
p {
	transform: skewX(24deg);
}
```
![[Pasted image 20220101152551.png]]

To skews the selected element along its Y(vertical) axis by a given degree by ```skewY()``` function from ```transform``` property. For example:
``` CSS
p {
	transform: skewY(-10deg);
}
```
![[Pasted image 20220101152836.png]]


# Graphic



# Padding of an Element
HTML elements are essentially little rectangles. There are three important properties control the space that surrounds each HTLM element: ```padding```, ```border```, ```margin```.

## Padding
An element's ```padding``` controls the amount of space between the element's content and its ```boarder```. For example: 

``` CSS
.blue-box {
	background-color: blue;
	color: #fff;
	padding: 20px;
}
```
![[Pasted image 20211231132250.png]]
When we increase the blue box's ```padding```, it will increase the distance(```padding```) between the text and the border around it. For example:

``` CSS
.blue-box {
	background-color: blue;
	color: #fff;
	padding: 5px;
}
```
![[Pasted image 20211231132615.png]]

### Different Padding to Each Side of an Element
If we want to customize an element so that is has different amount of ```padding``` on each of its sides. CSS allow us to control the ```padding``` of all four individual sides of an element with the ```padding-top```, ```padding-bottom```, ```padding-left``` and ```padding-right``` properties. For example:

``` CSS
.blue-box {
	background-color: blue;
	color: #fff;
	padding-top: 40px;
	padding-left: 40px;
	padding-right: 20px;
	padding_bottom: 20px;
}
```
![[Pasted image 20211231134823.png]]

#### Use Clockwise Notation
Instead of specifying and element's ```padding-top```, ```padding-bottom```, ```padding-left``` and ```padding-right``` properties individually, we can specify them all in one line, like this:

``` CSS
.blue-box {
	background-color: blue;
	color: #fff;
	padding: 10px 20px 10px 20px
}
```
The four values work like a clock: top, right, bottom, left.

## Margin
An element's ```margin``` controls the amount of space between elemen's ```border``` and surrounding elements. For example:

``` CSS
.blue-box {
	background-color: blue;
	color: #fff;
	padding: 20px;
	margin: 10px;
}
```
![[Pasted image 20211231132832.png]]
When we increase the blue box's ```margin```, it will increase the distance between its border and surrounding elements. For example:

``` CSS
.blue-box {
	background-color: blue;
	color: #fff;
	padding: 20px;
	margin: 30px;
}
```
![[Pasted image 20211231133112.png]]

### Negative Margin
If we want an element grow larger, we can set an element's margin to a negative value. For example:

``` CSS
.blue-box {
	background-color: blue;
	color: #fff;
	padding: 20px;
	margin: -15px;
}	
```
![[Pasted image 20211231134112.png]]

### Different Margin to Each Side of an Element
If we want to customize an element so that is has different amount of ```margin``` on each of its side. CSS allow us to control ```margin``` of  all four individual sides of an element with the ```margin-top```, ```margin-right```, ```margin-bottom``` and ```margin-left``` properties. For example: 

``` CSS
.blue-box {
	background-color: blue;
	color: #fff;
	padding: 20px;
	margin-left: 40px;
	margin-bottom: 20px;
	margin-top: 40px;
	margin-right: 20px;
}
```
![[Pasted image 20211231135428.png]]

#### Use Clockwise Notation
Instead of specifying an element's ```margin-top```, ```margin-right```, ```margin-bottom``` and ```margin-left``` properties individually, we can specify them all in one line, like this:

``` CSS
.blue-box {
	background-color: blue;
	color: #fff;
	margin: 10px 20px 10px 20px
}
```
The four values work like a clock: top, right, bottom, left.

## Center an Element Horizontally
To center a block element horizontally, one way is to set its ```margin to a value of auto```. 

This method work for image, too. Image are inline elements by default, but can be changed to block elements when we set the ```display``` property to ```block```.

For example:

``` css
div {
	margin: auto;
}

img {
	display: block;
	margin: auto;
}
```



# Text
## Text-align Property
Text is often a large part of web content. CSS has several options for how to align it with the ```text-align``` property. 

> ```text-align: justify;``` spaces the text so that each line has equal width;
> ```text-align: center;``` centers the text;
> ```text-align: right;``` right-aligns the text;
> ```text-align: left;``` (the default) left-aligns the text.

```css
p {
	text-align: justify;
}
```

## Text Bold
To make text bold, we can use the ```strong``` tag. With the ```strong``` tag, the browser applies the CSS of ```font-weight: bold;``` to the element. For example:

```html
<p>Hello <strong>World</strong></p>
```

## Underline Text
To underline text, we can use the ```u``` tag. With ```u``` tag, the browser applies the the CSS of ```text-decoration: underline;``` to the element. For example:

```html
<p>Hello <u>World</u></p>
```

## Italicize Text
To emphasize text, we can use the ```em``` tag. This display text as italicized, as the browser applies the CSS of ```font-style: italic;``` to the element. For example:

```html
<p>Hello <em>World</em></p>
```

## Strikethrough Text
To strikethrough text (a horizontal line cuts across the characters), we can use ```s``` tag. It shows a section of text is no longer valid.With ```s``` tag the browser applies the CSS of ```text-decoration: line-through;``` to the element. For example:
```html
<p>Hello <s>World</s></p>
```

## Text Transform
tThe ```text-transform``` property in CSS is used to change the appearance of text. Which is convenient way to make sure text on a webpage appears consistently, without haveing to change the text content of the actual HTML elements.
- ```lowercase```  "hello world"
-  ```uppercase```  "HELLO WORLD"
- ```capitalize```  "Hello World"
- ```initial```  Use the default value.
- ```inherit``` Use the ```text-transform``` value from the parent element.
- ```none``` **default**: use the original text 

For example:
``` CSS
H1 {
	text-transform: uppercase;
}
```

## Line Height
CSS offer ```line-height``` property to change the height of each line in a block of text. It changes the amount of vertical space that each line of text gets.

```css
p {
	line-height: 25px;
}
```

# Horizontal Line
we can use ```hr``` tag to add a horizontal line across the width of its containing element. For example:
``` html
<h1>Hello</h1>
<hr>
```

# Shadow
The ```box-shadow``` property applies one or more shadows to an element.
The ```box-shadow``` property takes values for:
- ```offset-x``` how far to push the shadow horizontally from the element.
- ```offset-y``` how far to push the shadow vertically from the element.
- ```blur-raidus```
- ```spread-radius```
- ```color```
The ```blur-radius```  and  ```spread-radius``` values are optional. Also multiple box0shadows can be created by using commas to separate properties of each ```box-shadow``` element. For example:
``` CSS
box-shadow: 0 10px 20px rgba(0,0,0,0.19), 0 6px 6px rgba(0,0,0,0.23);
```

# Opacity
The ```opacity``` property in CSS is used to adjust the opacity, or conversely, the transparency for an item.
> - A value of 1 is opaque (which isn't transparent at all)
> - A value of 0.5 if half see-through.
> - A value of 0 if completely transparent.

For example:
```CSS
.links {
	opacity: 0.7;
}
```

# Pseudo-classes
Pseudo-class is a keyword that can be added to selectors, in order to select a specific state of the element. For example the styling of anchor tag can be changed for its hover state using the ```:hover``` pseudo-class selector.

# Hover State
By using the ```:hover``` pseudo-class selector, we can change the styling of an anchor tag. For example:
``` css
a {
	color: #000;
}

a:hover {
	color: red;
}
```

## :: before and ::after
```::before``` create a pesudo-element that is the first child of the select element.
```::after``` create a pesudo-element that is the last child of the select element.
For example if we want to create a heart shape, first a ```::before``` class is used to add a rectangle to an element with the class:
``` CSS
.heart::before {
	content: "";
	background-color: yellow;
	border-radius: 25%;
	position: absolute;
	height: 50px;
	width: 70px;
	top: -50px;
	left: 5px;
}
```

For the ```::before``` and ```::after``` pseudo-element to function properly, they must have a defined ```content``` property. This property is used to add things like a photo or text to the select element. When the ```::before``` and ```::after``` pseudo-element are used to make shapes, the ```content``` property is still required, but it's set to an empty string.

 In the above example, the element with the class of `heart` has a `::before` pseudo-element that produces a yellow rectangle with height and width of `50px` and `70px`, respectively. This rectangle has round corners due to its 25% `border-radius` and is positioned absolutely at `5px` from the left and `50px` above the top of the element.

 ## Animation
 To animate an element, we need to use the animation properties and the ```@keyframes``` rule. The animation properties control how the animation should behave and the ```@keyframes``` rule controls what happens during that animation. There are eight animation properties in total. The two most important ones:

 ```animation-name``` sets the name of the animation, which is used by ```@keyframes``` to tell CSS which rules go with which animations.

 ```animation-duration``` set the length of time for the animation.

 ```@keyframes``` is how specify exactly what happens within the animation over the duration. This is done by given CSS properties for specify "frames" during the animation, with percentages ranging from 0% to 100%. The CSS properties for 0% is how the element element displays in the opening scene. The CSS properties for 100% is how the element appears at the end. For example:
```CSS
#anim {
	animation-name: colorful;
	animation-duration: 3s;
}

@keyframes colorful {
	0% {
		background-color: blue;
	}

	100% {
		background-color: yellow;
	}
}
```

For the element with ```anim``` id, the code snippet above set the ```animation-name``` to ```colorful``` and sets the ```animation-duration``` to 3 seconds. Then the ```@keyframes``` rule links to animation properties with the name ```colorful```. It sets the color to blue at the beginning of the animation (0%) which will transition to yellow by the end of the animation(100%).

## Specifies element when animation finished
If we don't want our animation reset after the duration, this can be done by setting the ```animation-fill-mode``` property to forward. The ```animation-fill-mode``` specifies the style applied to an element when the animation has finished. We can set it like so:
```CSS
#anim {
	animation-name: colorful;
	animation-duration: 3s;
	animation-fill-mode: forwards;
}

@keyframes colorful {
	0% {
		background-color: blue;
	}

	100% {
		background-color: yellow;
	}
}
```

## Movement Animation
When elements have a specified ```position```, such as ```fixed``` and ```relative```, the CSS offset properties ```right```, ```left```, ```top``` and ```bottom``` can be used in animation rules to create movement. For example:
``` CSS
@keyframes rainbow {
	0% {
		top: 0px;
	}
	50% {
		top: 50px;
	}
	100% {
		top: 0px;
	}
}
```

## Visual Direction 
``` CSS
@keyframes fade {
	50% {
		left: 60%;
		opacity: 0.1;
	}
}
```
In the displayed animation, the round element with the gradient background moves to the right by the 50% mark of the animation per the `@keyframes` rule.

## Animation Continually
Another animation property is the ```animation-iteration-count```, which allow us to control how many times we would like to loop through the animation. For example:
``` CSS
#anim {
	animation-name: colorful;
	animation-duration: 3s;
	animation-iteration-count: infinite;
}
```
By setting the ```animation-iteration-count``` property to ```infinite```, we make the animation run continuously.

## Animation Timing
In CSS animation, the ```animation-timing-function``` property controls how quickly an animated element change over the duration of the animation. If the animation is a car moving from point A to point B in a given time (```animation-duration```), the ```animation-timing-function``` says how the car accelerates and decelerates over the course of the drive.

```ease``` the default value, which starts slow, speeds up in the middle, and then slows down again in the end.
```ease-out```, which is quick in the beginning then slows down.
```ease-in```, which is slow in the beginning then speeds up at the end.
```linear```, which is applies a constant animation speed throughout.

For example: 
```CSS
#anim {
	animation-name: colorful;
	animation-duration: 3s;
	animation-iteration-count: infinite;
	animation-timing-function: ease;
}
```

# Cubic-bezier
CSS offer ```cubic-bezier``` function which provides even finer control over how the animation plays out than keywords.

In CSS animation, Bezier curvers are sued with the ```cubic-bezier``` function. The shape of the curve represents how the animation plays out. The curve lives on a 1 by 1 coordinate system. The X-axis of this coordinate system is the duration of the animation (a time scale), and Y-axis is the change in the animation.

The ```cubic-bezier``` function consists of four main points that sit on this 1 by 1 grid: ```p0```, ```p1```, ```p2``` and ```p3```. ```p0``` and ```p3``` are set for us - they are the beginning and end points which are always located respectively at the origin(0,0) and (1,1). We set the x and y values for the other two point, and where we place them in the grid dictates the shape of the curve for the animation to follow. This is done in CSS by declaring the x and y values of the ```p1``` and ```p2``` "anchor" point in the form: ```(x1, y1, x2, y2)```. Pulling it all together, here's an exaple:
``` CSS
animation-timing-function: cubic-bezier(0.25, 0.25, 0.75, 0.75);
```

### Move a Graphic
Similar animation progressions to the ```ease-out``` keyword can be achieved by using a custom cubic Bezier curve function.

In general, changing the ```p1``` and ```p2``` anchor point drives the creation of different Bezier curves, which controls how the animation progresses through time. Here's a example of a Bezier curve using values to mimic the ease-out style:
```css
animation-timing-function: cubic-bezier(0, 0, 0.58, 1);
```
Remember that all `cubic-bezier` functions start with `p0` at (0, 0) and end with `p3` at (1, 1). In this example, the curve moves faster through the Y-axis (starts at 0, goes to `p1` y value of 0, then goes to `p2` y value of 1) than it moves through the X-axis (0 to start, then 0 for `p1`, up to 0.58 for `p2`).

### Natural Motion
The ```animation-timing-function``` automatically loops at every keyframe when the ```animation-iteration-count``` is set to infinite. The following cubic Bezier curve simulates a juggling movement:
``` CSS
cubic-bezier(0.3, 0.4, 0.5, 1.6);
```