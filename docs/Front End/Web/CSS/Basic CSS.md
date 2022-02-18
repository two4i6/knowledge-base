---
aliases: [CSS, Basic CSS]
---

# CSS
With CSS there are hundreds of CSS properties that we can use to change the way an element looks on our page.

# Use CSS Selectors
We can styling element individually with inline CSS.
Such as:
``` HTML
<h1 style-"color: red;">Hello</h1>
```

That is one way to specify the style of an element, but there is a better way.
At the top of our code, create a ```style``` block look like this:
``` HTML
<style>
	...
</style>
```
Inside that style block, we can create a CSS selector for a element. For example, if we want all ```h1``` elements to be red:
``` HTML
<style>
	h1 {
		color: red;
	}
</style>
```
*note: that is important to have both opening and closing curly braces ```{``` and ```}``` around each element's style rules. 

## CSS Class Selector
Classes are reusable styles that can be added to HTML elements. Classes are always allow us to use the same CSS styles on multiple HTML elements.
Here's an example:
``` HTML
<style>
	.blue-text {
		color: blue;
	}
</style>
```
To apply this, we need add ```class="blue-text"``` to an HTML elements. And we are also able to apply multiple classes to an element using its ```class``` attribute, by separating each class name with a space.

*note: in our CSS ```style``` element, class name start with a period ```.```. In our HTML elements' class attribute, the class name does not include the period ```.```.

## ID Selector
In addition to classes, each HTML elements can also have an id attribute. An ```id``` has a higher specificity(importance) than a class.

There are several benefits to using ```id``` attributes: We can use an ```id``` to style a single element and we can use them to select and modify specific elements with JavaScript.

```id``` attributes should be unique. Browsers won't enforce this, but it is a widely agreed upon best practice.

For example:
``` CSS
<h2 id="cat-photo-app">
```
### Using ID Attribute to style an Element
```id``` just like ```class``` we can style them using CSS. To apply this, we have to put a ```#``` in front of their name. For example: 
``` CSS
#cat-photo-element {
	background-color: green;
}
```

## Attribute Selectors
We can use ```[attr=value]``` attribute selector to style element. For example, we want to style the radio button, this selector will match and style element with a specific attribute value:
``` CSS
[type="radio"] {
	margin: 20px 0px 20px 0px;
}
```

## Style the HTML Body
Every HTML page has a ```body``` element, and this element can also be styled with CSS. We can style our ```body``` element by:
``` CSS
body{
	background-color: black;
}
```

# CSS Variables
CSS Variables are a powerful way to change many CSS style properties at once by changing only one value. For example:
``` CSS
.penguin {
	--penguin-skin: black;
	--penguin-belly: gray;
	--penguin-beak: yellow;
}
	
.penguin-top {
	background: var(--penguin-skin, gray);
}
```

## Create a custom CSS Variable
To Create a CSS variable, we need to give it a name with two hyphens ```--``` in front of it and assign it a value like this:
``` CSS
.penguin {
	--penguin-skin: gray
}
```

## Use a custom CSS Variable
After create a CSS variable, we can assign its value to other CSS properties by referencing the name we give it, like this:
``` CSS
.penguin {
	--penguin-skin: gray
}
.penguin-top {
	background: var(--penguin-skin);
}
```

### Attach a Fallback value to a CSS Variable
For example:
``` CSS
.penguin {
	--penguin-skin: gray
}
.penguin-top {
	background: var(--penguin-skin, black);
}
```
*note: This will not work on IE browser. Rather, it is used so that the browser has a color to display if cannot find your variable. When working with CSS you will likely run into browser compatibility issues at some point. This is why it's important to provide browser fallbacks to avoid potential problems. 

#### Improve Compatibility with Browser Fallback
When your browser parses the CSS of a webpage, it ignores any properties that it doesn't recognize or support.  If you do want to provide a browser fallback, it's as easy as providing another more widely supported value immediately before your declaration. For example:
``` CSS
:root {
	--red-color: red;
}

.red-box {
	background: red;
	background: var(--red-color);
}
```
We adding another ```background``` declaration right before the existing declaration, this will improve the compatibility. 

## Inherit CSS Variables
When we create a variable, it is available for us to use inside the selector in which we create it. It also is available in any of that selector's descendants. This happen because CSS variables are inherited, just like ordinary properties.

To make use of inheritance, CSS variables are often defined in the ```:root``` element. It is a pseudo-class selector that match the root element of the document, usually the ```html``` element. By create our variables in ```:root```, they will be available globally and can be accessed from any other selector in the style sheet. For example: 
``` CSS
:root {
	--red-color: red;
}

.red-box {
	background: red;
	background: var(--red-color);
}
```

## Change a variable for a specific area
When we create our variable in ```:root``` they will set the value of that variable for the whole page. But we can overwrite these variables by setting them again within a specific element.
``` CSS
:root {
	--red-color: red;
}

body {
	backgound: var(--red-color);
}

.box {
	--red-color: white;
}

.red-box {
	background: red;
	background: var(--red-color);
}
```
The background of ```body``` will be red, but after we assign it to white, the background of ```red-box``` will display in white.

## Use a media query to change variable
CSS Variables can simplify the way use media queries. For example:
``` CSS
:root {
	--red-color: red;
	--red-size: 100px;
}

@media (max-width: 350px){
	:root {
		--red-color: white;
		--red-size: 200px;
	}
}

```

# Color
```color``` style property is responsible for the color of an element.
this look like:
``` CSS
p {
	color: red;
}
```
If we want a transparent color use ```transparent```.

## Hex Code for Specific color
If we want to specific color of our HTML element, we can use hex code. In CSS we can use 6 Hex digits to represent colors, two each for red(R), green(G), blue(B) components. For example ```#000000``` is black. Hex code give us a possibilities of more than 16 million colors.
*Hexadecimals(Hex) are base 16 numbers. This means it uses sixteen distinct symbols (0-9 and A to F).  The digital ```0``` is the lowest number in hex code, and represents a complete absence of color. The digital ```F``` is the highest number in hex code, and represents the maximum possible brightness. 
For example:
``` CSS
p {
	color: #000000;
}
```

### Use Abbreviated Hex Code 
Since it's difficult to remember hex code, we can shorten it. For example, red's hex code ```#FF0000``` can be shorted to ```#F00```. This shortened form fives one digit for red, one digit for green, and one digit for blue. This reduce the total number of possible colors to around 4,000. But browser will interpret ```#FF0000``` and ```#F00``` as exactly the same color. For example:
``` CSS
p {
	color: #000;
}
```

## Use RGB values to Color Elements
Another way we can represent colors in CSS is by using ```RGB``` values. For example, The ```RGB``` value for black looks like this: 
``` CSS
p {
	color: rgb(0, 0, 0);
}
```
Instead of using 6 hex code, with ```RGB``` we specify the brightness of each color with a number between 0 and 255.

## Use RGBA value for background-color
We can add ```background-color``` to the element holding the text we want to emphasize. ```RGBA``` is great to use in this case, as it allows us to adjust the opacity. This means we don't have to completely block out the background. For example:
```
p {
	background-color: rbga(45, 45, 45, 0.1)
}
```

## HSL
CSS3 introduced the ```hsl()``` property as an alternative way to pick a color by directly stating hue, saturation and lightness. 
**HUE** is what people generally think of as 'color'. In ```hsl()``` hue uses a color wheel concept instead of the spectrum, where the angle of the color on circle is given as a value between 0 and 360.

**Saturation** is the amount of gray in a color. A fully saturated color has no gray in it, and a minimally saturated color is almost gray. this is given as a percentage with 100% being fully saturated.

**Lightness** is the amount of white or black in a color. A percentage is given ranging from 0% (black) to 100%(white), where 50% is the normal color. 

For example:

``` CSS
dvi {
	background-color: hsl(120, 100%, 50%);
}
```

## Linear Gradient
CSS also provides the ability to use color transitions, as known as gradients on elements. This ability accessed through the ```background``` property's ```liner-gradient()``` function. For example:

``` CSS
backgound: linear-gradient(90deg, red, yellow, rgb(203,203,255));
```

The general syntax is: 
```css
background: linear-gradient(gradient_direction, color 1, color 2, color 3, ...);
```

### Striped Element by Linear Gradient
We can use the ```repeating-linear-gradient()``` function to create a striped element. The ```repeating-linear-gradient()``` function is very similar to ```linear-gradient()``` with the major difference that it repeats the specified gradient pattern. ```repeating-linear-gradient()``` accepts a variety of values. For example: 
``` CSS
background:
	repeating-linear-gradient(
	45deg,
	yellow 0px,
	yellow 40px,
	black 40px,
	black 80px
	);
}
```
```

# Font
## Font Size
Font size control by the  ```front-size``` CSS property. this look like this:
``` CSS
p {
	font-size: 30px;
}
```
![[Pasted image 20220101151427.png]]

## Background Image
The ```background``` property supports the ```url()``` function in order to link to an image of the chosen texture of pattern. For exmaple:
```CSS
body {
	background:
		url("https://cdn-media-1.freecodecamp.org/imgr/MJAkxbh.png");
}
```




# Font
## Font family
Font family control by the ```font-family``` CSS property. For example:
``` CSS
p {
	font-family: sans-serif; 
}
```

## Font Weight
The ```font-weight``` property sets how thick or thin characters are in a section of text. For example:
``` CSS
p{ 
	font-weight: 800;
}
```

## Import Font
If we want to specify non-standard, custom web fonts for use on our website, such as Google Font which is a free library of web fonts that we can use in our CSS by referencing the font's URL. 

For example if we want to import the Lobster font, to do this we have to add this.
``` CSS
<link href="https://fonts.googleapis.com/css?family=Lobster" rel="stylesheet" type="text/css">
```

Then we can use the Lobster font in our CSS by using Lobster as the family name:
``` CSS
p {
	font-family: Lobster, sans-serif;
}
```
*Note: The ```sans-serif``` is optional, and is a fallback font in case the other specified font is not available. Family name are case-sensitive and need to be wrapped in quotes if there is a space in the name. For example, we need quotes to use the ```"Open Sans"```, but not to use the ```sans-serif```.

# Size the Image
Using the ```width``` CSS property to controls an element's width. For example:
``` CSS
.image {
	width: 500px;
}
```

# Border 
CSS borders have properties like ```style```, ```color``` and ```width```. For example:
``` CSS
.thin-red-border {
	border-color: red;
	border-width: 5px;
	border-style: solid;
}
```

## Add Rounded Corner
We can round out those corners with CSS property called ```border-radius```. For example:
``` CSS
.thin-red-border {
	border-color: red;
	border-width: 5px;
	border-style: solid;
	border-radius: 10px;
}
```

### Make Circular Image with border-radius
For example:
``` CSS
.thin-red-border {
	border-color: red;
	border-width: 5px;
	border-style: solid;
	border-radius: 50%;
}
```

# Background
## Background Color
``` CSS
.green-background {
	background-color: green;
}
```

# Absolute Vs. Relative Units
Pixels ```px``` are a type of length unit, which is what tells the browser how to size or space an item. In addition to ```px```, CSS has a number of different length unit options that we can use. The two main types of length units are **absolute** and **relative**. 

**Absolute** units tie to physical units of length. For example, ```in``` and ```mm``` refer inches and millimetres, respectively. Absolute length units approximate the actual measurement on a screen, but there are some different depending on a screen's resolution.

**Relative** units, such as ```em``` or ```rem```, are relative to another length value. For example, ```em``` is based on the size of an element's font. If we use it to set the ```font-size``` property itself, it's relative to the parent's ```font-size```.

For example:
``` CSS
.box {
	padding 1.5em;
}
```

# Inherit Styles
All other elements will inherit our ```body``` element's style.

# Prioritize One Style Over Another
Sometime our HTML element will receive multiple styles that conflict with one another.
``` CSS
body {
	color: green;
}

.pink-color {
	color: pink;
}

<h1 class="pink-color">hello</h1>
```
The ```pink-color``` class will override the ```body``` class. This ```h1``` element will display in pink instead of green.

# Override Styles in Subsequent CSS
The order of ```class``` declarations in the ```style``` section is what is important. The latest declaration will always take precedence over the first. For example:
``` CSS
body {
	color: green;
}
.pink-color {
	color: pink;
}
.blue-color {
	color: blue;
}
<h1 class="pink-color blue-color">hello</h1>
```
The ```blue-color``` class will override the ```pink-color``` and the ```body``` class. This ```h1``` element will display in blue instead of green or pink.

# Override Class Declarations by ID attributes
We known an ```id``` has a higher specificity(importance) than a class. It doesn't matter whether we declare CSS ```class``` above or below, the ```id``` attribute will always take precedence. For example:
``` CSS
body {
	color: green;
}
#brown-color {
	color: brown;
}
.pink-color {
	color: pink;
}
.blue-color {
	color: blue;
}
<h1 class="pink-color blue-color" id="brown-color">hello</h1>
```
The ```brown-color```  ```id``` attribute will override all other class. This ```h1``` element will display in brown.

# Override Class Declaration with Inline Styles
There are other way that we can override CSS by inline style. For example:
``` CSS
body {
	color: green;
}
#brown-color {
	color: brown;
}
.pink-color {
	color: pink;
}
.blue-color {
	color: blue;
}
<h1 class="pink-color blue-color" id="brown-color" style="color:white;">hello</h1>
```
The ```style="color:white;"``` will override CSS classes and ids styles. This ```h1``` element will display in white.

# Override All other Style by using Important
There's one last way to override CSS. This is the most powerful method of all. In many situation, we will use a CSS Libraries. These may accidentally override our own CSS. So when we absolutely need to be sure that an element has specific CSS, we can use ```!important```. For example:
``` CSS
body {
	color: green; 
}
#brown-color {
	color: brown;
}
.pink-color {
	color: pink !important;
}
.blue-color {
	color: blue;
}
<h1 class="pink-color blue-color" id="brown-color" style="color:white;">hello</h1>
```
The ```color: pink !important;``` will override all other CSS styles. This ```h1``` element will display in pink.
