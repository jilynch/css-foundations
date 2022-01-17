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

## The Box Model

If a box has an outer display type of `block`, it will behave in the following ways: The box will break onto a new line.

- The box will extend in the inline direction to fill the space  available in its container. In most cases this means that the box will  become as wide as its container, filling up 100% of the space available.
- The `width` and [`height`](https://developer.mozilla.org/en-US/docs/Web/CSS/height) properties are respected.
- Padding, margin and border will cause other elements to be pushed away from the box

If a box has an outer display type of `inline`, then:

- The box will not break onto a new line.
- The [`width`](https://developer.mozilla.org/en-US/docs/Web/CSS/width) and [`height`](https://developer.mozilla.org/en-US/docs/Web/CSS/height) properties will not apply.
- Vertical padding, margins, and borders will apply but will not cause other inline boxes to move away from the box.
- Horizontal padding, margins, and borders will apply and will cause other inline boxes to move away from the box.

### Parts of the box

- **Content box**: The area where your content is displayed, which can be sized using properties like [`width`](https://developer.mozilla.org/en-US/docs/Web/CSS/width) and [`height`](https://developer.mozilla.org/en-US/docs/Web/CSS/height).
- **Padding box**: The padding sits around the content as white space; its size can be controlled using [`padding`](https://developer.mozilla.org/en-US/docs/Web/CSS/padding) and related properties.
- **Border box**: The border box wraps the content and any padding. Its size and style can be controlled using [`border`](https://developer.mozilla.org/en-US/docs/Web/CSS/border) and related properties.
- **Margin box**: The margin is the outermost layer,  wrapping the content, padding, and border as whitespace between this box and other elements. Its size can be controlled using [`margin`](https://developer.mozilla.org/en-US/docs/Web/CSS/margin) and related properties.

![Diagram of the box model](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/The_box_model/box-model.png)

### Standard CSS box model

If you give a box a `width` and a `height` attribute, this defines the width and height of the *content box*. Any padding and border is then added to that width and height to get the total size taken up by the box. The margin is not counted towards the actual size of the box 

```css
.box {
  width: 350px;
  height: 150px;
  margin: 10px;
  padding: 25px;
  border: 5px solid black;
}
```

The *actual* space taken up by the box will be 410px wide (350 + 25 + 25 + 5 + 5) and 210px high (150 + 25 + 25 + 5 + 5).

![Showing the size of the box when the standard box model is being used.](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/The_box_model/standard-box-model.png)

### Alternative CSS box model

Using this model, any width is the width of the visible box on the page, therefore the content area width is that width minus the width for the padding and border.

```css
.box {
  box-sizing: border-box;
}
```

```css
html {
  box-sizing: border-box;
}
*, *::before, *::after {
  box-sizing: inherit;
}
```

 To understand the thinking behind this, see [the CSS Tricks article on box-sizing](https://css-tricks.com/inheriting-box-sizing-probably-slightly-better-best-practice/).

### `display: inline-block`

An element with `display: inline-block` does a subset of the block things:

- The `width` and `height` properties are respected.
- `padding`, `margin`, and `border` will cause other elements to be pushed away from the box.

It does not, however, break onto a new line, and will only become larger than its content if you explicitly add `width` and `height` properties.

![inline-block](https://i0.wp.com/css-tricks.com/wp-content/uploads/2011/09/inline-block.png?resize=526%2C207&ssl=1)
