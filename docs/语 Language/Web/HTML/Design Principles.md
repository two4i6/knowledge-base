# [[Design Principles]]
There are many devices that can access the web, and they come in all shapes and sizes. Responsive web design is the practice of designing flexible websites that can respond to different screen sizes, orientations, and resolutions. We need to make our website look good, no matter what device they're viewed on.

# Media Query
Media Queries are new technique introduced in CSS3 that change the presentation of content based on different viewport sizes. The viewport is a user's visible area of a web page, and is different depending on the device used to access the site.

Media Queries consist of a media type, and if that media type matches the style of the document is displayed on, the styles are applied. We can have as many selectors and styles inside our media query as we want.

Here is an example of a media query that returns the content when the device's width is less than or equal to ```100px```:
```CSS
@media (max-widht: 100px) {
	/* CSS Rules */
}
```

and the following media query return the content when the devices's height is more than or equal to ```350px```:
``` CSS
@media (min-height: 350px) {
	/* CSS Rules */
}
```


# Image Responsive
To making images responsive with CSS, we need to add these properties on an image:
``` CSS
img {
	max-width: 100%
	height: auto;
}
```
The ```max-width``` of ```100%``` will make sure the image is never wider than the container it is in, and the ```height``` of ```auto``` will make the image keep its original aspect ratio.


# Retina Image for High-Resolutaion Display
The simplest way to make our images properly on High-Resolution Displays is to define their ```width``` and ```height``` values as only half of that the original file is. For example:
``` HTML
<style>
	img {
		height: 250px;
		width: 250px;
	}
</style>

<img src="logo500x500" alt="company logo">
```


# Make Typography Responsive
Instead of using ```px``` or ```em``` to size text, we can use viewport units fro responsive typography. Viewpoint units, like percentages, are relative units, but they are based off different items. Viewport units are relative to the viewport dimensions (width or height) of a device, and percentages are relative to the size of the parent container element.

The for different viewport unites are:
- ```vw``` (viewport width): ```10vw``` would be 10% of the viewport's width.
- ```vh``` (viewport height): ```3vh``` would be 3% of the viewport's height.
- ```vmin``` (viewport minimum): ```70vmin``` would be 70% of the viewport's smaller dimension (height or width).
- ```vmax``` (viewport maximum): ```100vmax``` would be 100% of the viewport's bigger dimension (height or width).

For example:
``` CSS
body {
	width: 30vw;
}
```