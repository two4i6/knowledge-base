---
aliases: [HTML, Basic HTML]
---


# [[Basic HTML|HTML]] Element
Most HTML elements have an opening tag and a closing tag.
``` <h1> Hello </h1>```

opening tag look like 
``` <h1> ```

closing tag look like
``` </h1> ```

*all HTML tags are writing in lowercase.

# Comment
Comment in HTML start with ```<!--``` and end with ```-->```

# Doctype of HTML Document
This should be include in every HTML document. At top of HTML document we should tell browser which version of HTML the page is using.

To tell the browser this information by adding the ```<!DOCTYPE...>```tag on the first line, where the ```...``` part is the version of HTML. For HTML5, we use ```<!DOCTYPE html>```. The ```!``` and uppercase ```DOCTYPE``` is important, especially for older browser, The ```html``` is not case sensitive.

Next, the rest of our HTML code needs to be wrapped in ```html``` tags. The opening ```<html>``` goes directly below the ```<!DOCTYPE html>``` line, and the closing ```</html>``` goes at the end of the page.

For Example:
``` HTML
<!DOCTYPE html>
<HTML>
	...
</HTML>
```

# Head and Body of HTML Document
Any makeup with information about your page would go into the ```head``` tag. Such as ```link```, ```meta```, ```title```, and ```style``` typically go inside the head element.

Any makeup with contact of the page (what display to users) would go into the ```body``` tag.

For example:
``` HTML
<!DOCTYPE html>
<html>
	<head>
		<meta />
		<title>...</title>
		...
	</head>
	<body>
		<div>
			...
		</div>
		...
	</body>
</html>
```


# Headline
Headline elements tell the browser about the structure of the website.

```h1``` elements are often used for main headings.
```h2``` elements are generally used for subheadings.
```h3 h4 h5``` elements to indicate different level of subheadings.

# Paragraph
```p``` elements are the preferred element for paragraph text on websites.
``` <p> hello paragraph </p>```
Web developer traditionally use lorem ipsum text as placeholder text, which is randomly scraped form a famous passage by Cicero Ancient Rome.

# Image
Add images to website by using the ```img```  elements, and point to a specific image's URL using the src attribute.

*This kind of elements are self-closing.

All ```img``` element **must have an ```alt``` attribute, the text inside and ```alt``` attribute is used for screen readers to improve accessibility and  is displayed if the image fails to load.

look like ```<img src="https://www.google.com/logo.jpg" alt="logo">```

# Link
Link to content outside of the web page by using the ```a``` anchor elements.
Anchor element need a destination web address called an ```href``` attribute, and also need anchor text.

look like ```<a href="https://www.google.com"> Google </a>```

*To open page in new window, add ```target="_blank"``` attribute.

## internal Link
assign a link's ```href``` attribute to a hash symbol ```#``` plus the value of the id attribute for the element.

``` HTML
<a herf="#contacts-header"> Contacts </a>
```

## nest link in Paragraph
```HTML
<p> 
	Here's the <a target="_bland" href="https://google.com">Google</a> page.	
</p>
```

## dead link
``` herf="#" ```

## nest link with image
```HTML
<a herf="https://google.com"><img src="https://google.com/logo.jpg" alt="google"></a>
```

# List
## Bulleted Unordered  List
Start with an opening ```<ul>``` element, followed by and number of ```<li> </li>``` elements, Finally, unordered lists closed by ```</ul>```
This look like: 
```HTML
<ul>
	<li> A </li>
	<li> B </li>
</ul>
```
## Ordered List
Start with an opening ```<ol>``` element, followed by any number of ```<li>``` elements, Finally, ordered list are closed with the ```<ol>``` tag.
This look like:
```HTML
<ol>
	<li> A </li>
	<li> B </li>
</ol>
```

# Form 
To submit data to the server using nothing more than pure HTML. We can do this by specifying an action attribute on the ```form``` element.
For example:
```HTML
<form action="/url-where-you-want-to-subemit-form-data">
	<input>
</form>
```
## Submit form
To send the data form the form to the URL we specified with the form ```action``` attribute, we have to add a ```submit``` button to the form.
This look like:
```HTML
<form action="/url-where-you-want-to-subemit-form-data">
	<input>
	<button type="submit">submit</button>
</form>
```

## Require a filed (html5)
To require a specific form filed so user will not be able to submit the form until they filled it out. To do this we just add the attribute ```required``` within the ```input``` element.
For example:
```HTML
<input type="text" required>
```

# Input
## Text Field
Use ```input```  elements, those elements are self-closing.
It look like:
```HTML
<input type="text">
```
### placeholder text
Placeholder text is what displayed in the ```input``` element before the user has inputted anything.
This look like:
```HTML
<input type="text" placeholder="hello">
```

## Radio Button
Using radio button for questions where we want user to only give us one answer of multiple options.
Radio buttons are a type of ```input```, and each radio button can be nested within its own ```label```. All related radio button should have the same ```name``` attribute to create a radio button group. By creating a radio button group, selecting any single radio button within the same group will automatically deselect the other radio buttons, which mean only one answer will be provided by the user.
For example:
```HTML
<label>
	<input type="radio" name="group">Indoor</input>
</label>
```
To set a ```for``` attribute on the ```label``` element, with a value that matches the value of the id attribute of the input element. This allows assistive technologies to create a linked relationship between the label and the related ```input``` element.
For example:
```HTML
<input id="indoor" type="radio" name="group">Indor</input>
<label for="indoor">Indoor</label>
```
or nest the ```input``` element within the label tags:
```HTML
<label for=="indoor"><input id="indoor" type="radio" name="group">Indoor</label>
```

## Checkbox
 Forms commonly use checkboxes for questions that may have more than one answers.
 Check box is a type of input.
 Each of the checkboxes can be nested within its own ```label``` element. By wrapping an ```input``` element inside of a label element it will automatically associate the checkbox input with the label element surrounding it. All related checkbox element should have the same ```name``` attribute.
 For Example:
 ```HTML
 <label for="obj"><input id="obj" type="checkbox" name="cat"> white cat</label>
 ```
 
 ## Value attribute with Radio button and Checkbox
 When the form gets submitted, the data is sent to the server and includes entries for the options selected. Inputs of type ```radio``` and ```checkbox``` will report their values from the value attribute.
 For example:
 ```HTML
 <label for="indoor">
 	<input id="indoor" value="indoor" type="radio" name="indoor-outdoor">indoor
 </label>
 
 <label for="outdoor">
 	<input id="outdoor" value="radio" type="checkbox" name="indoor-outdoor">outdoor
 </label>
 ```
 When submit the form with the indoor option selected, the form data will include the line: ```indoor-outdoor=indoor```. This is from the ```name``` and ```value``` attributes of the "indoor" input.
 If you omit the ```value``` attribute, the submitted form data uses the default value, which is on. So when user submit the form, the form data will include the line```indoor-outdoor=on```, which is not really useful.
 
 ## Check Radio Buttons and Checkboxes by default
 To do this, just add the ```checked``` attribute to the inside of an input element.
For example:
```HTML
<input type="radio" name="test-name" checked>
```
## Label Element
The ```label``` tag wraps the text for a specific form control item, usually the name or label for a choice. This ties meaning to the item and makes the form more readable. The ```for``` attribute on a ```label``` tag explicitly associates that ```label``` with the form control and is used by screen readers. 

The value of the ```for``` attribute must be the same as the value of the ```id``` attribute of the form control. For example:
``` HTML
<form>
	<label for="name">Name:</label>
	<input type="text" id="name" name="name">
</form>
```

## Fieldset Element
The ```fieldset``` tag surrounds the entire grouping of radio buttons, it often uses a ```legend``` tag to provide a description for the grouping, which screen reader read for each choice in the fieldset element. 

The ```fieldset``` wrapper and ```legend``` tag are not necessary when the choices are self-explanatory. Using a ```label``` with the ```for``` attribute for each radio button is sufficient.

Here is an example:
``` html
<form>
	<fieldset>
		<legend>make a choice</legend>
		<input id="one" type="radio" name="item" value="one">
		<input id="two" type="radio" name="item" value="two">	
		<input id="three" type="radio" name="item" value="three">
	</fieldset>
</form>
```




# Div Element
The ```div``` element, also known as a division element, is a general purpose container for other elements. The ```div``` element start with ```<div>``` and close it on another line with ```</div>```.

# HTML5 Elements
```main header footer nav video article section``` and others.
These tags give a descriptive structure to HTML, make HTML easier to read, and also help with Search Engine Optimization (SEO).
```main``` tag helps search engines and other developers to find the main contact of page.