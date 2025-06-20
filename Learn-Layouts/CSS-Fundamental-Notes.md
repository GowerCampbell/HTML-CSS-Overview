# Knotes on CSS Layouts from learnlayout.com (with Answers)

*Recommended By #100Devs - Class 3 Homework*

---

## No Layout

* When is it better to have no specific layout and just a single, flowing column of content?
    > It is better for simple, content-focused pages where a single, readable, top-to-bottom flow is sufficient. This is often the default and most usable layout for narrow screens like mobile devices.

* What are the different values for the `display` property, such as `inline`, `block`, `inline-block`, and `inherit`?
    > These are some of the most common values. Key values include:
    > - **`block`**: The element starts on a new line and takes up the full width available.
    > - **`inline`**: The element does not start on a new line and only takes up as much width as necessary.
    > - **`inline-block`**: The element is like `inline` in that it flows with text, but it can have a set `width` and `height` like a `block` element.
    > - **`none`**: The element is completely removed from the page layout.
    > - **`flex`**: Enables the Flexbox layout model for the element's children.
    > - **`grid`**: Enables the Grid layout model for the element's children.
    > - **`inherit`**: The element takes the `display` value of its direct parent.

* What does the `flex` value for the `display` property do?
    > It turns an element into a "flex container," enabling the modern Flexbox layout model. This makes it easy to align, distribute, and reorder the items within that container, even when their size is unknown or dynamic.

---

## The "display" Property

* How does the `display` property act as the primary controller of an element's layout behavior?
    > It fundamentally dictates how an element is rendered in the document's flow. It controls whether the element generates a box, whether it starts on a new line, and what layout model its children will use (e.g., block-and-inline flow, flex, or grid).

* Does every element have a default `display` value, and what determines whether its default is `block` or `inline`?
    > Yes, every HTML element has a default `display` value defined by the browser's default stylesheet (user agent stylesheet). This default is based on the element's semantic purpose (e.g., a `<div>` is for division/blocking, a `<span>` is for an inline span of text).

#### block
* Why is a `<div>` considered a `block-level` element?
    > By default, a `<div>` is a generic container used for grouping content and structuring a page. Its purpose as a structural block means it defaults to `display: block`, causing it to start on a new line and occupy the full available width.

* What are other common `block-level` elements, including newer HTML5 elements like `<header>`, `<footer>`, and `<section>`?
    > Other common block-level elements include `<p>`, `<h1>`-`<h6>`, `<ul>`, `<ol>`, `<li>`, `<form>`, and HTML5 structural elements like `<article>`, `<section>`, `<nav>`, `<header>`, and `<footer>`.

#### inline
* Why is `<span>` considered the standard `inline` element?
    > Because it is a generic, non-semantic container used for styling or grouping a small portion of text or content *within* a larger block, without breaking the flow of that content.

* How can an `inline` element, like `<span>`, wrap text within a paragraph without disrupting the paragraph's flow?
    > An inline element renders as part of the line of text it is inside. It doesn't force a line break before or after it, so it flows naturally with the surrounding text.

* Is the `<a>` element one of the most common `inline` elements?
    > Yes, the `<a>` (anchor) tag used for hyperlinks is one of the most common and recognizable `inline` elements.

#### none
* What is the purpose of setting `display: none;`?
    > Its purpose is to completely remove an element from the document. The element will not be rendered, it will not take up any space, and it will be inaccessible to screen readers. It's as if the element doesn't exist in the HTML.

* Are specialized elements like `<script>` not displayed on the page because they serve other purposes, such as running JavaScript?
    > Yes, precisely. Elements like `<script>`, `<style>`, `<head>`, and `<title>` have a default `display: none;` value in all browsers because their purpose is to provide metadata or functionality, not visual content.

#### Other Display Values
* What are other `display` values, such as `list-item` or `flex`?
    > `list-item` makes an element behave like a `<li>` list item, typically generating a bullet point. `flex` and `grid` are modern and powerful values that turn an element into a container for advanced layout systems.

#### Extra Credit
* How can you set `<li>` elements to be `display: inline` to create a horizontal menu?
    > By applying the CSS rule `li { display: inline; }`. This overrides the default `display: list-item;`, removing the bullet points and causing the list items to flow horizontally next to each other instead of vertically.

---

## margin: auto;

```css
#main {
  width: 600px;
  margin: 0 auto;
}
```

* Why does setting a `width` on a `block-level` element prevent it from stretching out to the full width of its container?
    > By default, a block-level element expands to fill the available horizontal space of its container. Explicitly setting a `width` overrides this default behavior, constraining the element to the specified dimension.

* When you set the left and right margins to `auto`, why does the element center horizontally within its container? How is the remaining space split evenly between the margins?
    > When a block-level element has a specified `width`, `auto` for the left and right margins tells the browser to automatically calculate and distribute the remaining horizontal space in the container. The browser splits this space equally between the left and right margins, resulting in perfect horizontal centering.

* What happens if the browser window becomes narrower than the element's specified width? Will the browser create a horizontal scrollbar?
    > Yes. If the container (like the browser window) becomes narrower than the element's fixed `width`, the browser cannot shrink the element. To show all the content, it will create a horizontal scrollbar on the page.

---

## max-width

```css
#main {
  max-width: 600px;
  margin: 0 auto;
}
```

* Why does using `max-width` instead of `width` improve a browser's handling of small window sizes?
    > `max-width` allows the element to be flexible. It will shrink to fit inside its container if the container becomes narrower than the `max-width` value (e.g., on a mobile screen), thus preventing a horizontal scrollbar and creating a more responsive design.

* Does using `max-width` allow a box to resize smaller but prevent it from becoming larger than the specified value?
    > Yes, that is its exact purpose. The element can be any width *up to* the `max-width` value, but it cannot exceed it.

---

## The Box Model

* When you set the `width` of an element, why might it appear visually bigger than the value you specified?
    > This happens because of the standard CSS box model. By default, the `width` property only applies to the content area. The element's total visible width is the sum of its `width`, `padding`, and `border`.

* Do an element's `border` and `padding` stretch the element's total dimensions beyond its specified `width`?
    > Yes. In the default box model, `padding` is added to the inside of the content area, and `border` is added outside the padding, both of which increase the final rendered size of the element.

```css
.simple {
  width: 500px;
  margin: 20px auto;
}

.fancy {
  width: 500px;
  margin: 20px auto;
  padding: 50px;
  border-width: 10px;
}
```
* In the example above, why is the `.fancy` div wider on the screen than the `.simple` div, even though both have `width: 500px;`?
    > The `.fancy` div's total width is its `width` (500px) + left/right `padding` (50px + 50px) + left/right `border` (10px + 10px), for a total of 620px. The `.simple` div has no padding or border, so its total width is just 500px.

* How does `padding` provide more space for the content within a box?
    > Padding creates empty space around the content area, inside the element's border. It acts as internal cushioning, pushing the content away from the border.

---

## box-sizing

* Since the default box model can be unintuitive, what does the `box-sizing: border-box;` property do?
    > It changes the box model. When `box-sizing: border-box;` is set on an element, its `width` and `height` properties include the content, `padding`, and `border`. The content area shrinks to accommodate any padding and borders you add.

* When `box-sizing: border-box;` is applied, does the `width` property include the `padding` and `border`?
    > Yes. If you set `width: 500px;`, the element's total visible width will be 500px, regardless of the padding or border size you apply.

```css
.simple {
  width: 500px;
  margin: 20px auto;
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}

.fancy {
  width: 500px;
  margin: 20px auto;
  padding: 50px;
  border: solid blue 10px;
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}
```
* With `box-sizing: border-box;` applied to both divs in the example, will their rendered widths now be the same?
    > Yes, Hooray! Both `.simple` and `.fancy` will now have a final rendered width of exactly 500px.

* Why are vendor prefixes like `-webkit-` and `-moz-` sometimes required?
    > They were required for older versions of browsers (`-webkit-` for Chrome/Safari, `-moz-` for Firefox) to use CSS features that were experimental at the time. For `box-sizing`, they are largely no longer needed in modern browsers but are often included for compatibility with much older browser versions.

---

## position

#### static
* When should an element's position be left as `static`?
    > This is the default value. An element should be left as `position: static` when it should simply follow the normal document flow without any special positioning rules.

* What does it mean for an element to be "not positioned"?
    > An element is "not positioned" if its `position` property is set to `static`. It cannot be moved with properties like `top`, `left`, `bottom`, `right`, and `z-index`, and it cannot act as an anchor for absolutely positioned child elements.

* If an element's position is set to anything other than `static`, is it then considered "positioned"?
    > Yes. An element with `position: relative`, `absolute`, `fixed`, or `sticky` is known as a "positioned" element.

#### relative
* How does `position: relative;` behave the same as `static` by default?
    > If you only set `position: relative;` and do not add any offset properties (`top`, `left`, etc.), the element will remain in its original place in the normal document flow, just like `position: static`.

* Why is it important to also set `top`, `right`, `bottom`, or `left` properties on a relatively positioned element?
    > These properties are what actually move the element. Without them, `position: relative` on its own has no visual effect on the element's location. Its main purpose, when used alone, is to become a positioning context for absolute children.

* How will a relatively positioned element be adjusted away from its normal position?
    > The `top`, `right`, `bottom`, and `left` properties specify an offset from its *original* position. For example, `left: 20px;` will move the element 20 pixels to the right of where it would normally be.

* Will other content adjust to fill the gap left by the element?
    > No. The space the element *would have* occupied in the normal document flow is preserved. Other elements are not affected and do not move into the gap.

#### fixed
* How can a `fixed` element be positioned relative to the viewport, ensuring it stays in the same place even when the page is scrolled?
    > By setting `position: fixed;`. This removes the element from the normal document flow and positions it relative to the browser window (the viewport). It will not move, even when the user scrolls the page.

* How can we ensure a fixed element doesn't leave a gap in the page flow from where it would have originally been?
    > `position: fixed` automatically removes the element from the document flow, so other elements will behave as if it isn't there. The "gap" is automatically closed.

* Does a fixed element "travel" with you as you scroll through the page content?
    > Yes. It remains in a fixed position on the screen, creating an effect like a persistent header, footer, or "Back to Top" button.

#### absolute
* When should `position: absolute;` be used?
    > It should be used when you want to place an element at a precise location *relative to a container*. It removes the element from the normal document flow.

* How does an absolutely positioned element position itself relative to its nearest "positioned" ancestor?
    > It scans up its parent elements until it finds one that has a `position` value of `relative`, `absolute`, `fixed`, or `sticky`. It then uses the padding-edge of that ancestor as its coordinate system for `top`, `left`, etc.

* If there is no positioned ancestor, will the element position itself relative to the document body or the initial viewport?
    > It will be positioned relative to the initial containing block, which is typically the `<html>` element (the viewport).

* How does an absolutely positioned element behave when the page is scrolled?
    > It will scroll along with the page, because it is positioned relative to a container that is part of the page. This is a key difference from `position: fixed`.

```html
<div class="relative">
  <div class="absolute">...</div>
</div>
```
```css
.relative {
  position: relative;
  width: 600px;
  height: 400px;
}

.absolute {
  position: absolute;
  top: 120px;
  right: 0;
  width: 300px;
  height: 200px;
}
```
* In the example above, how does making the parent element `position: relative;` contain the `absolutely-positioned` child?
    > Setting `position: relative` on the parent makes it a "positioned" element. The child with `position: absolute` now uses this parent as its positioning context. Therefore, `top: 120px` and `right: 0` are calculated from the parent's boundaries, not the page's.

* If the parent's position were `static`, how would the child "escape" and be positioned relative to the document body instead?
    > If the parent were `static`, it would be "not positioned". The child would ignore it and look further up the DOM tree for a positioned ancestor. If it finds none, it will position itself relative to the initial containing block (the viewport/`<html>` element).

---

### Position Example

```css
/* ... (CSS from prompt) ... */
```
* In this layout, is it important for the `<section>` to have a `margin-left` style to create room for the `<nav>`?
    > Yes, it is crucial. The `<nav>` is `position: absolute`, which removes it from the normal document flow. The `<section>` would otherwise take up the full width of the container, positioning its content underneath the `<nav>`. The `margin-left: 200px;` pushes the section's content over to make space.

* How can you prevent the `absolute` and `static` elements from overlapping?
    > By using margins or padding on the `static` element (`<section>`) to create an empty space for the `absolute` element (`<nav>`) to occupy, as shown in the example with `margin-left`.

* Why does this example work correctly when the `.container` is taller than the `<nav>`?
    > It works because the `position: relative` on the `.container` provides a containing block for the layout. As long as the container has enough height to hold its content, the layout appears stable.

* How could you ensure the `<nav>` would not overflow outside its container if it were taller?
    > If the `<nav>` was taller, it would overflow the `.container` by default. To prevent this, you could add `overflow: auto;` or `overflow: hidden;` to the `.container` element.

* When using a fixed footer, do you need to add a margin to the bottom of the `<body>` to prevent content from being hidden behind it?
    > Yes. Since a fixed footer is removed from the document flow, content at the bottom of the page can scroll underneath and be obscured by it. Adding `margin-bottom` (or `padding-bottom`) to the `<body>` or a main content wrapper ensures there is enough space at the end of the page so that all content can be scrolled into view above the footer.

---

## float

* Was the `float` property originally intended for wrapping text around elements like images?
    > Yes. Its original and primary purpose was to allow text to flow, or "wrap," around an image, similar to layouts seen in newspapers and magazines.

```css
img {
  float: right;
  margin: 0 0 1em 1em;
}
```

---

## clear

* How is the `clear` property used to control the behavior of floated elements?
    > The `clear` property specifies that an element cannot have a floating element next to it. It forces the element to move down below any floated elements on the specified side (`left`, `right`, or `both`).

* If a `<section>` element appears after a `<div>` that is floated left, how will the text content of the `<section>` surround the `<div>`?
    > The `<section>` element's box will sit below the div, but its line boxes (the lines of text) will shorten and wrap around the right side of the floated `<div>`.

* What if you wanted the `<section>` to appear fully *after* the floated element, rather than wrapping around it?
    > You would need to apply the `clear` property to the `<section>` element.

```css
.box {
  float: left;
  width: 200px;
  height: 100px;
  margin: 1em;
}
.after-box {
  clear: left;
}
```
* How does using the `clear` property (with a value of `left`) move the `.after-box` section below the floated `.box` div?
    > `clear: left` tells the browser that the top edge of the `.after-box` element must be below the bottom edge of any preceding left-floated elements. This effectively pushes it down to "clear" the floated `.box`.

* Can `clear` also be used with the values `right` and `both` to clear floats on different sides?
    > Yes. `clear: right` clears right-floated elements, and `clear: both` clears any floated elements, whether they are floated left or right. `clear: both` is the most commonly used value.

---

## The clearfix Hack

* How can you prevent a floated image from being contained within a parent `<div>` if the parent has no other content to give it height?
    > This happens because floating an element removes it from the normal flow, and its parent container no longer "sees" its height. This is known as a collapsing parent.

* How does applying the `overflow: auto;` property to a container serve as a "clearfix" hack to make it contain its floated children?
    > Setting `overflow` to anything other than `visible` (the default) establishes a new "block formatting context" (BFC). A BFC will always expand to contain any floats within it. `overflow: auto` or `overflow: hidden` are common choices for this hack.

* For compatibility with older browsers like IE6, why might you need to add `zoom: 1;` in addition to `overflow: auto;`?
    > Older versions of Internet Explorer did not have BFCs but had a similar proprietary concept called `hasLayout`. Setting `zoom: 1;` was one way to trigger `hasLayout` on an element, which had the side effect of making it contain its floats, similar to how a BFC works.

---

## float Layout Example

* Why have layouts historically been created using `float` properties, even when `position` is an alternative?
    > Because `float` was the first CSS property that allowed for multi-column layouts where content could flow around the columns. `position` removes elements from the flow entirely, making it difficult to create layouts where content below the columns reflows naturally. `float` was the best tool for the job before Flexbox and Grid were introduced.

```css
nav {
  float: left;
  width: 200px;
}
section {
  margin-left: 200px;
}
```
* Why might a "clearfix" be necessary on the container of these elements to ensure the layout is robust?
    > A clearfix would be necessary on the parent container to ensure it expands to wrap around the floated `<nav>`. Without it, if the `<section>` were shorter than the `<nav>`, the parent container would collapse to the height of the `<section>`, and any subsequent elements would appear incorrectly.

---

## Percent Width

* How can you use percentage values for `width` in CSS to create a responsive, fluid layout?
    > A percentage `width` is calculated relative to the width of the element's containing block. This allows elements to automatically resize as the browser window (or parent container) changes size, creating a fluid and responsive effect.

* How would you make an image take up exactly 50% of the width of its container?
    > By applying the CSS rule `img { width: 50%; }`.

* How can `min-width` or `max-width` be used to constrain how large or small an element with a percentage width can become?
    > You can combine them. For example, `width: 50%; max-width: 400px; min-width: 200px;` means the element will try to be 50% wide, but it will never get larger than 400px or smaller than 200px. This prevents content from becoming unreadably wide or squished.

#### Percent Width Layout
```css
nav {
  float: left;
  width: 25%;
}
section {
  margin-left: 25%;
}
```
* When setting a `<nav>` to a percentage width, how can you prevent the content from becoming too squished on narrow screens?
    > By using a media query to change the layout on smaller screens. For example, you could remove the float and set both the `<nav>` and `<section>` to `width: 100%` so they stack vertically.

* Why does the `<section>` need a `margin-left` that matches the `width` of the floated `<nav>`?
    > The `<nav>` is floated left and takes up 25% of the width. The `<section>`'s content would normally try to wrap around it, starting at the left edge of the container. The `margin-left: 25%;` pushes the entire `<section>` block over, creating a distinct column next to the nav rather than wrapping text into its space.

---

## Media Queries

* What is the basic strategy for creating a responsive design using media queries?
    > The strategy is to apply different CSS rules based on the characteristics of the device, most commonly the viewport width. You can define "breakpoints" (e.g., 600px) where the layout changes to better suit the screen size.

* How can a `min-width` media query be used to apply a layout (like a floated sidebar) only on screens wider than a certain size?
    > A `min-width` query applies styles only when the viewport is *wider* than the specified value. This is used in a "mobile-first" approach, where you define simple, single-column styles by default and then add more complex, multi-column layouts inside a `min-width` media query for larger screens.

* How can a `max-width` media query be used to apply different styles (like making navigation items inline) only on screens narrower than a certain size?
    > A `max-width` query applies styles only when the viewport is *narrower* than the specified value. This is used in a "desktop-first" approach, where you design for large screens first and then "fix" the layout for smaller screens inside a `max-width` media query.

```css
/* ... (CSS from prompt) ... */
```
* Where can one find more comprehensive documentation on using media queries?
    > The best and most reliable source is the [MDN Web Docs on Media Queries](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_media_queries/Using_media_queries).

---

## inline-block

* How can you create a grid of boxes that fills up the browser?
    > By setting the boxes to `display: inline-block` and giving them a width (often a percentage). They will then line up horizontally and wrap to the next line when they run out of space.

* For creating a grid system, which is the better or easier method: using `float` or `display: inline-block`?
    > `display: inline-block` is generally considered easier because it avoids the complexities of floats, such as needing to be `clear`ed and the issue of collapsing parent containers.

* What makes the `float` method more difficult than the `inline-block` method?
    > The `float` method is more difficult because it requires careful management of the `clear` property or using a "clearfix" hack on parent containers to ensure the layout doesn't break.

* Why is `inline-block` considered the "easy way" to create a grid of items?
    > Because the elements behave more intuitively. They flow like text (left-to-right, wrapping to the next line) but can be sized like blocks, and they don't cause parent containers to collapse.

* How can you provide support for `display: inline-block` in older browsers like IE6 and IE7?
    > The common hack for IE6/7 was to set `display: inline;` and then trigger IE's proprietary `hasLayout` property, for example by setting `zoom: 1;`. This mimicked some of `inline-block`'s behavior.

---

## inline-block Layout

* How does the `vertical-align` property affect `inline-block` elements?
    > Since `inline-block` elements flow on the same line like text, `vertical-align` can be used to control their alignment relative to each other on that line. For example, `vertical-align: top;` will align the tops of all the `inline-block` elements in a row.

* If you leave whitespace between `inline-block` elements in the HTML source, what visual gap will appear between the columns?
    > A space will appear between the elements, just as a space between words in a sentence creates a visual gap. This can be an issue when creating pixel-perfect grids, as the gap can throw off percentage-based width calculations.

* When using `inline-block` for columns, why is it necessary to set a `width` for each column?
    > By default, an `inline-block` element's width is determined by its content. To create a structured grid or column layout, you must explicitly set the `width` of each column (e.g., `width: 25%`).

---

## column

* How can you use CSS properties like `column-count` to automatically create multi-column text layouts?
    > The `column-count` property tells the browser to take the content of an element and flow it into a specified number of columns automatically. Properties like `column-gap` and `column-rule` provide further styling options.

* What browsers do the vendor prefixes `-moz-` and `-webkit-` represent?
    > `-moz-` is for Mozilla Firefox. `-webkit-` is for browsers using the WebKit engine, such as older versions of Google Chrome, Safari, and Opera.

* Since CSS columns are a newer feature, why is it important to include these vendor prefixes for maximum browser compatibility?
    > Prefixes were needed when browsers first implemented the feature experimentally. Including them ensures that older browsers that only understood the prefixed version will still render the columns correctly. For modern browsers, the standard `column-count` property works.

* Where can you find more information about browser support for CSS columns?
    > Authoritative sources like [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/CSS/column-count) or [CanIUse.com](https://caniuse.com/multicolumn) provide detailed compatibility tables for all major browsers.

---

## flexbox

* How has Flexbox redefined the way layouts are created in CSS, and which browsers support the modern specification?
    > Flexbox introduced a much more powerful and logical model for distributing space and aligning items within a container. It made tasks that were difficult with floats (like vertical centering or equal-height columns) trivial. All modern browsers (Chrome, Firefox, Safari, Edge) have full support for the modern Flexbox specification.

* How can you tell if a tutorial or piece of code is using an old, outdated version of Flexbox versus the modern syntax?
    > You can tell by the property names.
    > - **Old (2009):** `display: box;` and properties like `box-orient`.
    > - **Tweener (2011):** `display: flexbox;` and functions like `flex()`.
    > - **Modern (Current):** `display: flex;` and properties like `flex-direction`, `justify-content`, and `align-items`.

#### Simple Layout using flexbox
* How can you use `display: flex` to create a simple two-column layout?
    > You create a container `div` and set it to `display: flex;`. The direct children of that container automatically become "flex items" and will align horizontally by default.

* What does the `flex: 1;` property do to a column?
    > `flex: 1;` is shorthand for `flex-grow: 1;`, `flex-shrink: 1;`, and `flex-basis: 0%;`. It tells a flex item to grow and shrink as needed, taking up any available free space in the container. If multiple items have `flex: 1;`, they will share the free space equally.

#### Fancy Layout using Flexbox
* In a Flexbox layout, what is the functional difference between `flex: initial`, `flex: none`, `flex: 1`, and `flex: 2`?
    > - **`flex: initial` (or `flex: 0 1 auto`):** The default value. The item shrinks if necessary but does not grow. Its size is based on its content.
    > - **`flex: none` (or `flex: 0 0 auto`):** The item is completely inflexible. It will not grow or shrink and will be sized based on its content.
    > - **`flex: 1`:** The item is fully flexible and will grow to take up available space.
    > - **`flex: 2`:** The item is also fully flexible, but it will try to take up twice as much of the available free space as an item with `flex: 1`.

#### Centering using Flexbox
* How can Flexbox be used to perfectly center an item both vertically and horizontally within its container?
    > By setting the container to `display: flex;` and then applying two properties: `justify-content: center;` (for horizontal centering) and `align-items: center;` (for vertical centering).

* What do the `align-items` and `justify-content` properties do?
    > - **`justify-content`**: Aligns flex items along the main axis (horizontally, by default). Values include `flex-start`, `flex-end`, `center`, `space-between`, and `space-around`.
    > - **`align-items`**: Aligns flex items along the cross axis (vertically, by default). Values include `flex-start`, `flex-end`, `center`, `stretch`, and `baseline`.

---

## CSS Frameworks

* What is the Pure CSS framework and where can it be found?
    > It's a set of small, responsive CSS modules that can be used to build websites and web apps, created by Yahoo. You can find it at [pure-css.github.io](https://purecss.io/).

* What is the Semantic UI framework and where can it be found?
    > It's a development framework that helps create beautiful, responsive layouts using human-friendly HTML with a focus on semantic class names. You can find it at [semantic-ui.com](https://semantic-ui.com/).

* What is the Foundation framework and where can it be found?
    > It's a family of responsive front-end frameworks that make it easy to design beautiful responsive websites, apps and emails that look amazing on any device. You can find it at [get.foundation](https://get.foundation/).

* What is the Susy grid system and where can it be found?
    > It's a powerful, custom-built grid layout engine for Sass that allows for flexible and complex grid systems without being restrictive. You can find it at [www.oddbird.net/susy/](https://www.oddbird.net/susy/).

* What is the Unsemantic framework and where can it be found?
    > It's a fluid grid system that is the successor to the 960 Grid System. It works in a similar way, but using percentages instead of pixels. You can find it at [unsemantic.com](https://unsemantic.com/).

---

## About This Site

* What is the purpose of the website learnlayout.com?
    > Its purpose is to teach the fundamentals of CSS layout by explaining concepts like `display`, `position`, `float`, and Flexbox in a simple, hands-on, and easy-to-digest way.
