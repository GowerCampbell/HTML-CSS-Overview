
# Positioning Content

Positioning in CSS structures designs and makes content digestible by controlling how elements are placed on a webpage. Key techniques include **floats**, **inline-block**, and **position** properties.

## Positioning with Floats
The `float` property removes an element from the normal document flow, positioning it to the left or right of its parent, allowing content to wrap around it (e.g., an `<img>` next to a `<p>`).

```css
img {
  float: left;
}
```

### Floats in Practice
Floats are used to create layouts like columns.

```html
<header>
  <code>&lt;header&gt;</code>
</header>
<section>
  <code>&lt;section&gt;</code>
</section>
<aside>
  <code>&lt;aside&gt;</code>
</aside>
<footer>
  <code>&lt;footer&gt;</code>
</footer>
```

```css
code {
  background: #2db34a;
  border-radius: 6px;
  color: #fff;
  display: block;
  font: 14px/24px "Source Code Pro", Inconsolata, "Lucida Console", Terminal, "Courier New", Courier;
  padding: 24px 15px;
  text-align: center;
}
header,
section,
aside,
footer {
  margin: 0 1.5% 24px 1.5%;
}
footer {
  margin-bottom: 0;
}
```

To create a two-column layout:
```css
section {
  float: left;
  margin: 0 1.5%;
  width: 63%;
}
aside {
  float: right;
  margin: 0 1.5%;
  width: 30%;
}
```

For a three-column layout:
```css
section {
  float: left;
  margin: 0 1.5%;
  width: 30%;
}
footer {
  clear: both;
  margin-bottom: 0;
}
```

**Note**: Floated elements become block-level, even if they were inline, allowing `width` and `height` properties.

## Clearing & Containing Floats
Floats can disrupt layouts if not cleared or contained, affecting margins and padding.

### Clearing Floats
The `clear` property prevents elements from wrapping around floated elements.
```css
div {
  clear: left; /* Clears left floats */
}
footer {
  clear: both; /* Clears both left and right floats */
}
```

### Containing Floats (Clearfix)
A **clearfix** contains floats within a parent element, ensuring it renders correctly without affecting the document flow outside.

```css
.group:before,
.group:after {
  content: "";
  display: table;
}
.group:after {
  clear: both;
}
.group {
  clear: both;
  *zoom: 1; /* For older browsers like IE */
}
```

Example:
```html
<header>...</header>
<div class="group">
  <section>...</section>
  <aside>...</aside>
</div>
<footer>...</footer>
```

```css
.group:before,
.group:after {
  content: "";
  display: table;
}
.group:after {
  clear: both;
}
.group {
  clear: both;
  *zoom: 1;
}
section {
  float: left;
  margin: 0 1.5%;
  width: 63%;
}
aside {
  float: right;
  margin: 0 1.5%;
  width: 30%;
}
```

This technique, known as a **clearfix**, organizes multiple sections or asides within a layout.

## Positioning with Inline-Block
The `inline-block` display allows elements to sit next to each other on the same line while respecting `width`, `height`, `padding`, `border`, and `margin`.

```css
section {
  display: inline-block;
  margin: 0 1.5%;
  width: 30%;
}
```

**Issue**: Inline-block elements include whitespace from HTML, which can push elements to a new row. Solutions:
1. **Remove Whitespace in HTML**:
   ```html
   <section>...</section><section>...</section><section>...</section>
   ```
2. **Use Comments to Eliminate Whitespace**:
   ```html
   <section>...</section><!--
   --><section>...</section><!--
   --><section>...</section>
   ```

## Creating Reusable Layouts
Floats or inline-block can create grid-like layouts. Modern CSS specifications like **Flexbox** and **Grid** are now preferred for advanced layouts.

### Example HTML
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>Styles Conference</title>
    <link rel="stylesheet" href="./assets/stylesheets/main.css">
  </head>
  <body>
    <header class="container group">
      <section class="container">
        <h1 class="logo">
          <a href="index.html">Styles <br> Conference</a>
        </h1>
      </section>
      <h3>August 24–26th — Chicago, IL</h3>
      <nav>
        <a href="index.html">Home</a>
        <a href="speakers.html">Speakers</a>
        <a href="schedule.html">Schedule</a>
        <a href="venue.html">Venue</a>
        <a href="register.html">Register</a>
      </nav>
    </header>
    <section class="hero container">
      <h2>Dedicated to the Craft of Building Websites</h2>
      <p>Every year the brightest web designers and front-end developers descend on Chicago to discuss the latest technologies. Join us this August!</p>
      <a href="register.html" class="btn btn-alt">Register Now</a>
    </section>
    <section class="grid">
      <!-- Speakers -->
      <section class="col-1-3">
        <a href="speakers.html">
          <h5>Speakers</h5>
          <h3>World-Class Speakers</h3>
        </a>
        <p>Joining us from all around the world are over twenty fantastic speakers, here to share their stories.</p>
      </section><!--
      Schedule
      --><section class="col-1-3">
        <a href="schedule.html">
          <h5>Schedule</h5>
          <h3>Three Inspiring Days</h3>
        </a>
        <p>Enjoy three inspiring and action-packed days of talks, gatherings, and all-around good times.</p>
      </section><!--
      Venue
      --><section class="col-1-3">
        <a href="venue.html">
          <h5>Venue</h5>
          <h3>The Chicago Theatre</h3>
        </a>
        <p>Within the heart of downtown Chicago, The Chicago Theatre will provide a beautiful conference venue.</p>
      </section>
    </section>
    <footer class="primary-footer container group">
      <small>© Styles Conference</small>
      <nav>
        <a href="index.html">Home</a>
        <a href="speakers.html">Speakers</a>
        <a href="schedule.html">Schedule</a>
        <a href="venue.html">Venue</a>
        <a href="register.html">Register</a>
      </nav>
    </footer>
  </body>
</html>
```

### Example CSS
```css
.container,
.grid {
  margin: 0 auto;
  width: 960px;
}
.container {
  padding-left: 30px;
  padding-right: 30px;
}
.grid,
.col-1-3,
.col-2-3 {
  padding-left: 15px;
  padding-right: 15px;
}
.col-1-3,
.col-2-3 {
  display: inline-block;
  vertical-align: top;
}
.col-1-3 {
  width: 33.33%;
}
.col-2-3 {
  width: 66.66%;
}
```

## Uniquely Positioning Elements
The `position` property allows precise control over element placement.

### Relative Positioning
Elements remain in the normal document flow but can be offset without affecting surrounding elements.
```html
<div>...</div>
<div class="offset">...</div>
<div>...</div>
```

```css
div {
  height: 100px;
  width: 100px;
}
.offset {
  left: 20px;
  position: relative;
  top: 20px;
}
```
The `.offset` div shifts 20px right and down, overlapping others without altering their positions.

### Absolute Positioning
Elements are removed from the normal flow and positioned relative to the nearest **positioned** ancestor (e.g., with `position: relative`). If none exists, it’s relative to the `<body>`.

```html
<section>
  <div class="offset">...</div>
</section>
```

```css
section {
  position: relative;
}
div {
  position: absolute;
  right: 20px;
  top: 20px;
}
```

This positions the `div` 20px from the top-right of the `<section>`, useful for placing elements within a container.

