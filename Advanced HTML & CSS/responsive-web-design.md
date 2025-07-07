# Responsive Web Design

Building websites for all users. Mobile internet usage has surpassed desktop usage, driving the growth of responsive design.

## Responsive Overview

[Read more here](https://alistapart.com/article/responsive-web-design/) — credited to Ethan Marcotte.

> "Building a foundation to define its fame and shape its facade, creative decisions quite literally shape a digital space."

Ensuring consistent windows and screen resolutions, user preferences, and user-installed fonts — but the landscape is changing from a flexible foundation.

> "I love programming because I can bring stuff into existence."

---

## Responsive vs Adaptive vs Mobile

### Responsive

Create declarations that react to changes in factors like viewport width.

### Adaptive

Modified for a new purpose or situation, built to fit a set of predefined factors.

### Mobile

Building a separate website, accessible only to mobile users. Comes with dependencies of a new code base.

---

## Flexible Layouts

### Components

- **Media Queries**
- **Flexible Media**

### Flexible Layouts

Use grids that dynamically resize to any width, built using relative length units (percentages or `em`). These relative lengths are then used to declare properties such as width, margin, or padding.

CSS3 introduced new relative units:

- `vw`: viewport width
- `vh`: viewport height
- `vmin`: minimum of the viewport's height and width
- `vmax`: maximum of the viewport's height and width

Flexible layouts do not use fixed measurements (e.g., pixels or inches), as viewport sizes vary.

#### Proportion Formula

```

target ÷ context = result

````

### Example Flexible Grid

```html
<div class="container">
  <section>...</section>
  <aside>...</aside>
</div>
````

```css
.container {
  width: 538px;
}

section, aside {
  margin: 10px;
}

section {
  float: left;
  width: 350px;
}

aside {
  float: right;
  width: 158px;
}
```

Converted to relative units:

```css
section, aside {
  margin: 1.858%; /* 10px ÷ 538px = 0.01858 */
}

section {
  float: left;
  width: 63.197%; /* 340px ÷ 538px = 0.63197 */
}

aside {
  float: right;
  width: 29.36%; /* 158px ÷ 538px = 0.2936 */
}
```

---

## Media Queries

Media queries target different devices or browser states by specifying styles depending on viewport width, device orientation, etc.

[CSS Tricks Guide](https://css-tricks.com/css-media-queries/)

### Initializing Media Queries

HTML:

```html
<link href="style.css" rel="stylesheet" media="all and (max-width: 1024px)">
```

CSS:

```css
@media all and (max-width: 1024px) { ... }

@import url(styles.css) all and (max-width: 1024px);
```

#### Media Types

* all (default)
* screen
* print
* tv
* braille
* (others, including 3d-glasses)

#### Logical Operators

* `and`
* `not`
* `only`

Examples:

```css
@media all and (min-width: 800px) and (max-width: 1024px) { ... }

@media not screen and (color) { ... }

@media only screen and (orientation: portrait) { ... }
```

---

## Media Features

### Height & Width

```css
@media all and (min-width: 320px) and (max-width: 780px) { ... }
```

### Orientation

```css
@media all and (orientation: landscape) { ... }
```

### Aspect Ratio

```css
@media all and (min-device-aspect-ratio: 16/9) { ... }
```

### Pixel Ratio

```css
@media only screen and (-webkit-min-device-pixel-ratio: 1.3), only screen and (min-device-pixel-ratio: 1.3) { ... }
```

### Resolution

```css
@media print and (min-resolution: 300dpi) { ... }
```

### Color and Grid

* `color`
* `color-index`
* `monochrome`
* `grid`

**Note:** Media queries are not supported in IE8 and below. Use polyfills like `respond.js` or `CSS3-MediaQueries.js` for support.

---

## Media Queries Demo

```css
@media all and (max-width: 420px) {
  section, aside {
    float: none;
    width: auto;
  }
}
```

---

## Identifying Breakpoints

Common breakpoints:

* 320px
* 480px
* 768px
* 1024px
* 1224px

---

## Mobile First

Use smaller viewports by default and progressively enhance for larger screens.

```css
@media screen and (min-width: 400px)  { ... }
@media screen and (min-width: 600px)  { ... }
@media screen and (min-width: 1000px) { ... }
@media screen and (min-width: 1400px) { ... }
```

---

## Example: Mobile First Demo

```css
section,
aside {
  margin: 1.8587%;
}

@media all and (min-width: 420px) {
  .container {
    max-width: 538px;
  }
  section {
    float: left;
    width: 63.197%;
  }
  aside {
    float: right;
    width: 29.368%;
  }
}
```

---

## Viewport

### Meta Tag

```html
<meta name="viewport" content="width=device-width">
```

### Scale Control

```html
<meta name="viewport" content="initial-scale=2">
<meta name="viewport" content="minimum-scale=0">
<meta name="viewport" content="user-scalable=yes">
<meta name="viewport" content="target-densitydpi=device-dpi">
<meta name="viewport" content="width=device-width, initial-scale=1">
```

---

## CSS Viewport Rule

```css
@viewport {
  width: device-width;
  zoom: 1;
}
```

---

## Flexible Media

```css
img, video, canvas {
  max-width: 100%;
}
```

### Flexible Embedded Media

```css
figure {
  height: 0;
  padding-bottom: 56.25%; /* 16:9 */
  position: relative;
  width: 100%;
}

iframe {
  height: 100%;
  left: 0;
  position: absolute;
  top: 0;
  width: 100%;
}
```

---

## Conclusion

A fully responsive approach ensures your website scales and adapts to all screen sizes, devices, and orientations while maintaining usability and aesthetic quality.
