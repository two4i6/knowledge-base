# [[Applied Accessibility]] 
In web development, accessibility refer to web content and a user interface that can be understood, navigated, and interacted with by a broad audience. This include people with visual, auditory, mobility, or cognitive disabilities.


# Text Alternative to Image
Remember good ```alt``` text provides the reader a brief description of the image. We should always include an ```alt``` attribute on our image.
``` HTML
<img src="logo.png" alt="company logo">
```

## Know When Alt Text Should be Left Blank
However, sometimes images are grouped with a caption already describing them, or are used for decoration only. In these cases, ```alt``` text may seem redundant or unnecessary. So when an image is already explained with text content or does not add meaning to page, the ```img``` still need an ```alt``` attribute, but it can be set to an empty string. Here is an example:
``` HTML
<img src="product.png" alt="">
```

# Use Headings to Show Hierarchical Relationships of Content
Heading (```h1``` to ```h6``` elements) are workhorse tags that help provide structure and labeling to our content. Screen reader can beset to read only the headings on a pages so the user gets a summary. This means it's important for the heading tags in your markup to have semantic meaning and relate to each other, not be picked merely for their size value.

*Semantic meaning* means that the tag you use around content indicates the type  of information it contains.

Headings with equal (or higher) rank start new implied sections, headings with lower rank start subsections of the previous one.

As an example, a page with an `h2` element followed by several subsections labeled with `h4` elements would confuse a screen reader user. With six choices, it's tempting to use a tag because it looks better in a browser, but you can use CSS to edit the relative sizing.

One final point, each page should always have one (and only one) `h1` element, which is the main subject of your content. This and the other headings are used in part by search engines to understand the topic of the page.

# Jump Straight to the Content Using the main Element
HTML5 introduced several new element that give developers more options while also incorporating accessibility features. These tags include ```main, header, footer, nav, article and section``` among other.

By default, a browser renders these elements similar to the humble ```div```. However, using them where appropriate gives additional meaning to our makeup. The tag name alone can indicate the type of information it contains, which adds semantic meaning to that content.

The ```main``` element is used to wrap the main content, and there should be only one per page. It's meant to surround the information related to our page's central topic. It's not meant to include items that repeat across pages, like navigation links or banners.

The ```main``` tag also has an embedded landmark feature that assistive technology can use to navigate to the main content quickly (things like "jump to Main Content" Link).

# Wrap content in the article element
```article``` is another one of the new HTML5 elements that add semantic meaning to your markup. ```article``` is sectioning element and is used to wrap independent, self-contained content. The tag works well with blog entires, forum posts, or news articles. For example:
``` html
<article>
	<h2> Hello </h2>
	<p> Content </p>
</article>
```

```section``` element is also new with HTML5, and has a slightly different semantic meaning than ```article```. An ```article``` is for standalone content, and a ```section``` is for grouping thematically related content. For example, if a book is the ```article```, then each chapter is a ```section```. When there's no relationship between groups of content, then use a ```div```.

# Make Screen Reader Navigation Easier with header Landmark
The ```header``` tag is used to wrap introductory information or navigation links for its parent tag and works well around content that's repeated at the top on multiple pages. ```header``` also have embedded landmark feature. For example:
``` HTML
<header> 
	<h1> Hello </h1>
</header>
```

# Navigation 
The ```nav``` tag is meant to wrap around the main navigation links in our page. It also have embedded landmark feature. For example:
``` HTML
<header>
	<ul>
		<li><a href="#a">a</li>
		<li><a href="#b">a</li>
	</ul>
</header>
```

# Footer
The ```footer``` tag is meant to wrap around the content of copyright information or links to related document that usually sit at the bottom of a page. It also have embedded landmark feature. For example:
``` HTML
<footer>
	&copy; 2021 Hello
<footer>
```

# Audio
HTML5's ```audio``` element gives semantic meaning when it wraps sound or audio stream content in our markup. Audio content also needs a text alternative to be accessible to people who are deaf or hard of hearing. This can be done with nearby text on the page or link to a transcript.

The ```audio``` element support the ```controls``` attribute. This shows the browser default play, pause, and other controls, and supports keyboard functionality. This is a boolean attribute, its presence on the tag turns the setting on.

For example:
```HTML
<audio controls>
	<source src="audio/xx.mp3" type="audio/mpeg">
</audio>
```

# Figure Element
HTML5's ```figure``` element and the related ```figcaption```, used together, these items wrap a visual representation (like an image, digram, or chart) along with its caption. For data visualizations like charts, the caption can be used to briefly note the trends or conclusion for users with visual impairments.

For example:
``` HTML
<figure>
	<img src="logo.png" alt="company logo">
	<figcaption>
		Hello World
	</figcaption>
</figure>
```

# Date
## Date Picker
Form often include the ```input``` field, which can be used to create several different form controls. The ```type``` attribute on this element indicates what kind of ```input``` element will be created.

And HMTL5 introduced an option to specify a ```date``` field. A data picker shows up in the ```input``` field when it's in focus, which makes filling in a form easier for all users.

For older browsers, the type will default to ```text```, so it helps to show users the expected data format in the ```label``` or ```placeholder``` text just in case.

Here is an example:
``` html
<label for="input1">Enter a date:</label>
<input type="date" id="input1" name="input1">
```

## Datatime Attribute
HTML5 introduced the ```time``` element along with a ```datatime``` attribute to standardize times. The ```time``` element along with a ```datatime``` attribute to standardize times. The ```time``` element is an inline element that can wrap a date or time on a page. A ```datatime``` attribute holds a valid format of that date. This is the value accessed by assistive devices.

Here's an example:
```HTML
<p>Today is <time datetime="2013-02-13">last Wednesday</time>. </p>
```

# Only Visible to a Screen Reader
```
.box {
	overflow: hidden;
}
```
The following CSS approaches will NOT do the same thing:
- ```display: none``` or ```visibility: hidden;``` hides content for everyone, including screen reader users.
- Zero values for pixel sizes, such as ```width: 0px; height: 0px;``` remove that element from the flow of our document, meaning screen reader will ignore it.

# Avoid Colorblindness Issues
## **Using Sufficient Contrast**
The WCAG-recommended contrast ratio of 4.5:1 applies for color use as well as gray-scale combinations. For exmaple:
``` CSS
body {
	color: hsl(0, 55%, 15%);
	background-color: hsl(120, 25%, 55%);
}
```


# Keyboard Accessibility
## Access Keys 
HTML offers the ```accesskey``` attribute to specify a shortcut key to activate or bring focus to an element. Adding an ```accesskey``` attribute can make navigation more efficient for **keyboard users**. For example:
```html
<button accesskey="b">Important Button</button>
<a href="#" accesskey="m">ME</a>
```

## Tabindex
The HTML ```tabindex``` attribute has three distinct functions relating to an element's keyboard focus. When it's on a tag, it indicates that the element can be focused on.  The value (an integer that's positive, negative, or zero) determines the behavior.

Certain element, such as links and form controls, automatically receive keyboard focus when a user tabs through a page. It's in the same order as the elements come in the HTML source markup. This same functionality can be given to other elements, such as ```div```, ```span```, and ```p```, by placing a ```tabindex="0"``` attribute on them. For example:
```html
<div tabindex="0">I need keyboard focus!</div>
```
![[Pasted image 20220102015514.png]]

A negative `tabindex` value (typically -1) indicates that an element is focusable, but is not reachable by the keyboard.  This method is generally used to bring focus to content programmatically (like when a `div` used for a pop-up window is activated), and is beyond the scope of these challenges.

