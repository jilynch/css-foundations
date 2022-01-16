# The Odin Project CSS Foundations.

-   [CSS Foundations](#css-foundations)
-   [Inspection HTML and CSS](#inspecting-html-and-css)
-   [The Box Model](#the-box-model)
-   [Block and Inline](#block-and-inline)

## CSS Foundations

### Basic Syntax

![css-basic-syntax](https://user-images.githubusercontent.com/70952936/130702428-4808becb-cbc4-4a4d-8fa7-f9aa5409768d.jpg)

### Selectors

It is a pattern of elements and other terms that tell the browser which HTML elements should be selected to have the CSS property values inside the rule applied to them.

-   Universal Selectors ( \* )

The universal selector will select elements of any type.

```css
* {
	color: purple;
}
```

-   Type/Element Selectors ( html element )

A type selector (or element selector) will select all elements of the given element type.

```css
div {
	color: white;
}
```

-   Class Selectors ( . )

Class selectors will select all elements with the given class.

```html
<!-- index.html -->
<div class="alert-text">Please agree to our terms of service.</div>
```

```css
/* styles.css */
.alert-text {
	color: red;
}
```

-   ID Selectors ( #html id )

ID selectors will select an element with the given ID.

```html
<!-- index.html -->
<div id="title">My Awesome 90's Page</div>
```

```css
/* styles.css */
#title {
	background-color: red;
}
```
