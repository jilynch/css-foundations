# The Odin Project CSS Foundations.

-   [CSS Foundations](#css-foundations)
-   [Inspection HTML and CSS](#inspecting-html-and-css)
-   [The Box Model](#the-box-model)
-   [Block and Inline](#block-and-inline)

## CSS Foundations

### Adding CSS to HTML

#### External CSS

```html
<!-- index.html -->

<head>
  <link rel="stylesheet" href="styles.css">
</head>
```

#### Internal CSS

```html
<head>
  <style>
    div {
      color: white;
      background-color: black;
    }

    p {
      color: red;
    }
  </style>
</head>
<body>...</body>
```

#### Inline CSS

```css
<body>
  <div style="color: white; background-color: black;">...</div>
</body>
```



### Basic Syntax

![css-basic-syntax](https://user-images.githubusercontent.com/70952936/130702428-4808becb-cbc4-4a4d-8fa7-f9aa5409768d.jpg)

### Selectors

It is a pattern of elements and other terms that tell the browser which HTML elements should be selected to have the CSS property values inside the rule applied to them.

| Selectors    |       |                                                 |
| ------------ | :---: | ----------------------------------------------- |
| Universal    |  `*`  | Selects elements of any type.                   |
| Type/Element | `div` | Selects all elements of the given element type. |
| Class        |  `.`  | Selects all elements with the given class.      |
| ID           |  `#`  | Selects an element with the given ID.           |

### Specificity

1. ID Selectors (most specific selector).
2. Class Selectors.
3. Type Selectors.

### Grouping Selectors

```css
.read, 
.unread {
  color: white;
  background-color: black;
}
```

### Chaining Selectors

```html
<div>
  <div class="subsection header">Latest Posts</div>
  <p class="subsection preview">This is where a preview for a post might go.</p>
</div>
```

```css
.subsection.header {
  color: red;
}
```

What `.subsection.header` does is it selects any element that has both the `subsection` *and* `header` classes.

### Descendant Combinator

A descendant combinator  will only cause elements that match the last selector to be selected if  they also have an ancestor (parent, grandparent, etc) that matches the  previous selector.

So something like `.ancestor .child` would select an element with the class `child` if it has an ancestor with the class `ancestor`.

```html
<!-- index.html -->

<div class="ancestor"> <!-- A -->
  <div class="contents"> <!-- B -->
    <div class="contents"> <!-- C -->
    </div>
  </div>
</div>

<div class="contents"></div> <!-- D -->
```

```css
/* styles.css */

.ancestor .contents {
  /* some declarations */
}
```



### Inheritance

Inheritance refers to certain CSS properties that, when applied to an  element, are inherited by that element’s descendants, even if we don’t  explicitly write a rule for those descendants. Typography based  properties (`color`, `font-size`, `font-family`, etc.) are usually inherited, while most other properties aren’t.
