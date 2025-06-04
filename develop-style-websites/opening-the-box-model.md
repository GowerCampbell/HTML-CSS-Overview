
# Opening the Box Model

The box model defines how elements are displayed and sized on a webpage. Every element is a rectangular box, with properties like width, height, padding, border, and margin determining its size and positioning.

## Block vs. Inline Elements
- **Block-Level Elements**:
  - Occupy the full available width, regardless of content.
  - Start on a new line, stacking vertically.
  - Examples: `<div>`, `<p>`, `<section>`.
- **Inline-Level Elements**:
  - Occupy only the width required by their content.
  - Line up on the same line, flowing with the document.
  - Examples: `<span>`, `<a>`, `<strong>`.

## Display Property
The `display` property controls how an element behaves.

```css
p {
  display: block; /* Default for <p>, starts on a new line, full width */
}
p {
  display: inline; /* Flows inline with other content */
}
p {
  display: inline-block; /* Behaves like inline but respects width/height */
}
```
**Result of `inline-block`**: Paragraph one. Paragraph two. Paragraph three (on the same line).

```css
div {
  display: none; /* Hides the element, rendering the page as if it doesn’t exist */
}
```

## Box Model
Every element is a rectangular box with the following components:
- **Content**: The inner content (text, images, etc.).
- **Padding**: Space inside the border, around the content.
- **Border**: Surrounds the padding.
- **Margin**: Space outside the border.

Example:
```css
div {
  border: 6px solid #949599;
  height: 100px;
  margin: 20px;
  padding: 20px;
  width: 400px;
}
```

### Width & Height
- **Total Width**: `margin-right + border-right + padding-right + width + padding-left + border-left + margin-left`.
  - Example: `20px + 6px + 20px + 400px + 20px + 6px + 20px = 492px`.
- **Total Height**: `margin-top + border-top + padding-top + height + padding-bottom + border-bottom + margin-bottom`.
  - Example: `20px + 6px + 20px + 100px + 20px + 6px + 20px = 192px`.

```css
div {
  width: 400px;
  height: 100px;
}
```

- **Block-Level Elements**: Default width is 100% of the parent’s available space. Height is determined by content.
- **Inline-Level Elements**: Do not accept `width` or `height` properties; they expand/contract based on content.

### Margin & Padding
- **Margin**: Space outside the border, used to position elements. Transparent, showing the background of the parent element.
  ```css
  div {
    margin: 20px; /* Applies 20px to all sides */
  }
  ```
- **Padding**: Space inside the border, around the content. Shows the element’s background color.
  ```css
  div {
    padding: 20px; /* Applies 20px to all sides */
  }
  ```

**Note**: For inline-level elements:
- Margins work only horizontally (left/right).
- Padding works on all sides, but vertical padding (top/bottom) bleeds into the lines above/below.

#### Shorthand vs. Longhand Declarations
- **Shorthand**:
  ```css
  div {
    margin: 10px 20px; /* Top/bottom: 10px, left/right: 20px */
  }
  div {
    margin: 10px 20px 0 15px; /* Top: 10px, right: 20px, bottom: 0, left: 15px */
  }
  ```
- **Longhand**:
  ```css
  div {
    margin-top: 10px;
    padding-left: 6px;
  }
  ```

### Borders
Borders require `width`, `style`, and `color`.
```css
div {
  border: 6px solid #949599; /* Width, style, color */
}
```
Styles: `solid`, `dotted`, `dashed`, `double`.

Target specific sides:
```css
div {
  border-bottom: 6px solid #949599;
}
div {
  border-bottom-width: 12px;
}
```

#### Border Radius
Rounds the corners of an element.
```css
div {
  border-radius: 5px; /* Applies to all corners */
}
div {
  border-top-right-radius: 5px; /* Targets specific corner */
}
```

## Box Sizing
The `box-sizing` property changes how the box model calculates an element’s size. Options:
- **Content-Box** (default): Width/height only include the content. Padding and border add to the total size.
  ```css
  div {
    -webkit-box-sizing: content-box;
       -moz-box-sizing: content-box;
            box-sizing: content-box;
  }
  ```
- **Border-Box**: Width/height include content, padding, and border. Margins are still added.
  ```css
  div {
    box-sizing: border-box;
  }
  ```
- **Padding-Box**: No longer supported in modern CSS.

**Vendor Prefixes**: Used for browser compatibility (e.g., `-webkit-` for Chrome/Safari, `-moz-` for Firefox).

**Choosing Box Sizing**: `border-box` is preferred for predictable sizing, as padding and borders don’t increase the element’s size. It supports mixed length units but isn’t universally supported in older browsers.

## Developer Tools
Use browser developer tools to inspect elements and debug styles. The sidebar provides insights into applied styles, box model calculations, and more.

## Practice

### HTML
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>Styles Conference</title>
    <link rel="stylesheet" href="./assets/stylesheets/main.css">
  </head>
  <body>
    <header class="container">
      <section class="container">
        <h1><a href="index.html">Styles Conference</a></h1>
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
    <section>
      <a href="speakers.html">
        <h5>Speakers</h5>
        <h3>World-Class Speakers</h3>
      </a>
      <p>Joining us from all around the world are over twenty fantastic speakers, here to share their stories.</p>
    </section>
    <footer class="container">
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

### CSS
```css
/* http://meyerweb.com/eric/tools/css/reset/ 2. v2.0 | 20110126
   License: none (public domain)
*/
html, body, div, span, applet, object, iframe,
h1, h2, h3, h4, h5, h6, p, blockquote, pre,
a, abbr, acronym, address, big, cite, code,
del, dfn, em, img, ins, kbd, q, s, samp,
small, strike, strong, sub, sup, tt, var,
b, u, i, center,
dl, dt, dd, ol, ul, li,
fieldset, form, label, legend,
table, caption, tbody, tfoot, thead, tr, th, td,
article, aside, canvas, details, embed,
figure, figcaption, footer, header, hgroup,
menu, nav, output, ruby, section, summary,
time, mark, audio, video {
  margin: 0;
  padding: 0;
  border: 0;
  font-size: 100%;
  font: inherit;
  vertical-align: baseline;
}
/* HTML5 display-role reset for older browsers */
article, aside, details, figcaption, figure,
footer, header, hgroup, menu, nav, section {
  display: block;
}
body {
  line-height: 1;
}
ol, ul {
  list-style: none;
}
blockquote, q {
  quotes: Juno
}
table {
  border-collapse: collapse;
  border-spacing: 0;
}

/*
  ========================================
  Grid
  ========================================
*/
*,
*:before,
*:after {
  -webkit-box-sizing: border-box;
     -moz-box-sizing: border-box;
          box-sizing: border-box;
}
.container {
  margin: 0 auto;
  padding-left: 30px;
  padding-right: 30px;
  width: 960px;
}

/*
  ========================================
  Typography
  ========================================
*/
h1, h3, h4, h5, p {
  margin-bottom: 22px;
}

/*
  ========================================
  Buttons
  ========================================
*/
.btn {
  border-radius: 5px;
  display: inline-block;
  margin: 0;
}
.btn-alt {
  border: 1px solid #dfe2e5;
  padding: 10px 30px;
}

/*
  ========================================
  Home
  ========================================
*/
.hero {
  padding: 22px 80px 66px 80px;
}
```

