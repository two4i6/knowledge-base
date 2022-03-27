# [[CSS Grid]]
CSS Grid is a newer standard that makes it easy to build complex responsive layouts. It works by turning an HTLM element into a grid, and lets you place child elements anywhere whiten.

Turn any HTML element into a grid container by setting its ```display``` property to ```grid```. This give us the ability to use all the other properties associated with CSS Grid.

*note: In CSS Grid, the parent element is referred to as the container and its children are called items. 

```CSS
.container {
	display: grid;
}
```
![[Pasted image 20220102175652.png]]


# Add Columns
To add some columns to the grid, use the ```grid-template-columns``` property on a grid container as demonstrated bellow:

``` CSS
.container {
	display: grid;
	grid-template-columns: 100px 100px 100px; 
}
```
![[Pasted image 20220102180020.png]]This give our grid two columns that are each 100px wide. The number of parameters given to the ```grid-template-columns``` property indicates the number of columns in the grid, and the value of each parameter indicates the width of each column.


# Add Rows
To adjust the rows manually, use the ```grid-template-rows``` property in the same way we used ```grid-template-columns```.

``` CSS
.container {
	display: grid;
	grid-template-columns: 100px 100px 100px;
	grid-template-rows: 100px 50px;
}
```
![[Pasted image 20220102180419.png]]


# Change Size of Columns and Rows
We can use absolute and relative units like ```px``` and ```em``` in CSS Grid to define the size of rows and columns. We can use these as well:

```fr``` sets the column or row to fraction of the available space.

```auto``` sets the column or row to the width or height of tis content automatically.

```%``` adjust the column or row to the percent width of tis container.

``` CSS
gird-template-columns: auto 50px 10% 2fr 1fr;
```
![[Pasted image 20220102181045.png]]
This snippet creates five columns. The first column is as wide as its content, the second column is 50px, the third 10% of its container, and for the last two columns, the remaining space is divided into three sections, two are allocated for the fourth column, and one for the fifth.


# Add Column Gaps
To add a gap between the columns, use the ```grid-column-gap``` property like this:
``` CSS
grid-column-gap: 20px;
```
![[Pasted image 20220102182042.png]]


# Add Row Gap
To add a gap in between rows of a grid using ```grid-row-gap``` property like this:
``` CSS
grid-row-gap: 5px;
```
![[Pasted image 20220102182401.png]]


# Add Gaps Faster 
```grid-gap``` is a shorthand property for ```grid-row-gap``` and ```grid-column-gap```. If ```grid-gap``` has one value, it will create a gap between all rows and columns. However, if there are two values, it will use the first one to set the gap between the rows and the second value for the columns.

``` CSS
gird-gap: 10px 20px;
```
![[Pasted image 20220102182721.png]]



# Use grid-column to Control Spacing
The ```grid-column``` property is the first one for use on the grid items themselves.

The hypothetical horizontal and vertical lines that create the grid are referred to as lines, These lines are numbered starting with 1 at the top left corner of the grid and move right for columns and down for rows. It look like for a 3x3 grid:
![[Pasted image 20220102184319.png]]

To control the number of columns an item will consume, we can use the ```grid-column``` property in conjunction with the line numbers we want the item to start and stop at.

Here's an example:
``` CSS
.item5 {
	grid-column: 2 / 4;
}
```
![[Pasted image 20220102184743.png]]




# Use grid-row to Control Spacing
We define the horizontal lines we want an item to start and stop at using the ```grid-row``` property on a grid item.
``` CSS
.item5 {
	grid-column: 2 / 4;
	grid-row: 2 / 4;
}
```
![[Pasted image 20220102185044.png]]


# Align A Item
## Align items Horizontally
In CSS Grid, the content of each item is located in a box which is referee to as a cell. We can align the content's position within its cell horizontally using the ```justify-self``` property on a grid item. By default, this property has a value of ```stretch```, which will make the content fill the while width of the cell. This CSS Grid property accepts other values as well:

- ```start``` aligns the content at the left of the cell.
- ```center``` aligns the content in the center of the cell.
- ```end``` aligns the content at the right of the cell.

``` CSS
.item2 {
	justify-self: center;
}
```
![[Pasted image 20220102190015.png]]

## Align items Vertically
We can use the ```align-self``` property on an item, this property accepts all of the same values as ```justify-self```.

``` CSS
.item2 {
	align-self: end;
}
```
![[Pasted image 20220102190320.png]]


# Align All Items
## Align All Items Horizontally
When we want all the items in our CSS Grid to share the same alignment. We can align them all at once horizontally by using Justify-items by using ```justify-items``` on our grid container. This property can accept all the same values we use in ```align-self``` or ```justify-self```.

``` CSS
.container {
	justify-items: center;
}
```
![[Pasted image 20220102210334.png]]


## Align All items Vertically
Using the ```align-items``` property on a grid container will set the vertical alignment for all the items in our grid.

``` CSS
.container {
	align-items: center;
}
```

![[Pasted image 20220102210802.png]]


# Grid Areas
## Divide the Grid Into an Area Template
We can group calls of our grid together into an *area* and give the area a custom name. Do this by using ```grid-template-areas``` on the container like this:

``` CSS
	.contaier {
		grid-template-areas:
		"header header header"
		"advert content content"
		"footer footer footer"
	}
```
The code above groups the cells of the grid into four areas:
```header```, ```advert```, ```content``` and ```footer```. Every word represents a cell and every pair of quotation marks represent a row.

## Place Items in Grid Areas
After creating an area template for our grid container, we can place an item in our custom area by referencing the name we gave it. To do this, we use the ```grid-area``` property on an item like this:

``` CSS
.item5 {
	grid-area: footer;
}
```

This lets the grid know that we want the ```item1``` class to go in the area named ```footer```. 
![[Pasted image 20220102212304.png]]


## Using grid-area without creating an Areas Template
The ```grid-area``` property can be used in another way. If we doesn't have an area template to reference, we can create an area on the fly for an item to be placed like this:

``` CSS
.item5 {
	grid-area: 1/1/2/4;
}
```

This is using the line number to define where the area for this item will be. The number in the example above represent these values:

```css
grid-area: horizontal line to start at / vertical line to start at / horizontal line to end at / vertical line to end at;
```
So the item in the example will consume the rows between lines 1 and 2, and the columns between 1 and 4.

For example:
``` CSS
.item5 {
	grid-area: 3/1/4/4;
}
```
In the above example, we place the element with `item5`class between the third and fourth horizontal lines and between the first and fourth vertical lines.
![[Pasted image 20220102213122.png]]


# Reduce Repetition
When we used ```grid-template-coulumns``` and ```grid-template-rows``` to define the structure of a grid, we enters a value for each row or column we created.

By using the ```repeat``` function to specify the number of times we want our column or row to be repeated, followed by a comma and the value we want to repeat.

Here is an example that would create the 100 row grid, each row at ```50px``` tall.

```CSS
grid-template-rows: repeat(100, 50px);
```

We can also repeat multiple values with the repeat function and insert the function amongst other values when defining a grid structure. Here's what looks like:

```CSS
grid-template-row: repeat(2, 1fr, 50px) 20px;
```
This translate to:
```CSS
grid-template-row: 1fr 50px 1fr 50px 20px;
```

```CSS
grid-template-columns: repeat (3, 1fr);
grid-template-rows: repeat (3, 1fr);
```

![[Pasted image 20220102214804.png]]


# Limit Item Size
There's another built-in function to use with `grid-template-columns` and `grid-template-rows` called `minmax`. It's used to limit the size of items when the grid container changes size. To do this we need to specify the acceptable size range for our item. For example:

``` CSS
grid-template-columns: 100px minmax(50px, 200px);
```

In the code above, ```grid-template-columns``` is set to create two columns; The first is 100px wide, and the second has the minimum width of 50px and the maximum width of 200px.

```CSS
grid-template-columns: repeat(3, minmax(90px, 1fr));
```


# Flexible Layout
## Using auto-fill
The repeat function comes with an option called auto-fill. This allows us to automatically insert as many rows or columns of our desired size as possible depending on the size of the container. We can create Flexible layouts when combining ```auto-fill``` with ```minmax```, like this:

``` CSS
grid-template-columns: repeat(auto-file, minmax(60px, 1fr));
```

When the container changes size, this setup keeps inserting 60px columns and stretching them until it can insert another one.

![[Pasted image 20220102221311.png]]


## Using auto-fit
```auto-fit``` is almost identically to ```auto-fill```. The only different is that when the container's size exceeds the size of all the items combined.
```auto-fill``` keeps inserting empty rows or columns and pushes our items to the side.
```auto-fit``` collapses those empty rows or columns and stretches our items to fit the size of the container.

```CSS
grid-template-columns: repeat(auto-fit, minmax(60px, 1fr));
```


# Using Media Queries
``` CSS
@media (min-width: 300px){
	.container{
	grid-template-columns: auto 1fr;	
	grid-template-rows: auto 1fr auto;
	grid-template-areas:
	"advert header"
	"advert content"
	"advert footer";
	}
}
```
![[Pasted image 20220102222831.png]]

```CSS
@media (min-width: 400px){
.container{
	grid-template-areas:
		"advert header"
		"advert content"
		"advert footer";
	}
}
```
![[Pasted image 20220102222842.png]]



# Create a Grids within Grids
``` CSS
display: grid;
grid-template-columns: auto 1fr;
```