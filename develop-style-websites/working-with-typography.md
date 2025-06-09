
# Typography Guide for Web Design

## Typeface vs. Font
- **Typeface**: The visual design of the text, what you see (e.g., Helvetica, Times New Roman).
- **Font**: The file containing the typeface, used to render the typeface on a device.

## Adding Color to Text
Set the color of text within an element using the `color` property in CSS.

```css
html {
  color: #555;
}
```

## Font-Based Properties
CSS provides several properties to style fonts:

### Font Family
Specify the typeface and fallback fonts.
```css
body {
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
}
```

### Font Size
Set the size using pixels, em units, percentages, points, or keywords.
```css
body {
  font-size: 14px;
}
```

### Font Style
Use `normal`, `italic`, `oblique`, or `inherit`.
```css
.special {
  font-style: italic;
}
```

### Font Variant
Set to `normal`, `small-caps`, or `inherit`.
```css
.firm {
  font-variant: small-caps;
}
```

### Font Weight
Set to `normal`, `bold`, `bolder`, `lighter`, `inherit`, or numeric values (100–900).
```css
.daring {
  font-weight: 600; /* Semibold */
}
```

### Line Height
Set line spacing using pixels, percentages, or unitless values (e.g., 1.5).
```css
body {
  line-height: 22px;
}
```
Center text vertically within an element.
```css
.btn {
  height: 22px;
  line-height: 22px;
}
```

### Shorthand Font Property
Combine `font-style`, `font-variant`, `font-weight`, `font-size`, `line-height`, and `font-family`.
```css
html {
  font: italic small-caps bold 14px/22px "Helvetica Neue", Helvetica, Arial, sans-serif;
}
```

## Example: Font Properties in Action
```html
<h2><a href="#">I Am a Builder</a></h2>
<p class="byline">Posted by Shay Howe</p>
<p>Every day I see designers and developers working alongside one another...</p>
```

```css
h2, p {
  color: #555;
  font: 13px/20px "Helvetica Neue", Helvetica, Arial, sans-serif;
}
a {
  color: #0087cc;
}
a:hover {
  color: #ff7b29;
}
h2 {
  font-size: 22px;
  font-weight: bold;
  margin-bottom: 6px;
}
.byline {
  color: #9799a7;
  font-family: Georgia, Times, "Times New Roman", serif;
  font-style: italic;
  margin-bottom: 18px;
}
```

## Text-Based Properties

### Text Align
Align text using `left`, `right`, `center`, `justify`, or `inherit`.
```css
p {
  text-align: center;
}
```

### Text Decoration
Apply `none`, `underline`, `overline`, `line-through`, or `inherit`.
```css
.note {
  text-decoration: underline;
}
```

### Text Indent
Indent the first line of text (positive indents inward, negative indents outward).
```css
p {
  text-indent: 15px;
}
```

### Text Shadow
Add shadows with horizontal offset, vertical offset, blur radius, and color.
```css
p {
  text-shadow: 3px 6px 2px rgba(0, 0, 0, 0.3);
}
```
Multiple shadows can be chained with commas.

### Box Shadow
Similar to `text-shadow`, applies to the element’s box, with an optional `inset` value.
```css
p {
  box-shadow: 3px 3px 5px rgba(0, 0, 0, 0.2);
}
```

### Text Transform
Transform text to `none`, `capitalize`, `uppercase`, `lowercase`, or `inherit`.
```css
p {
  text-transform: uppercase;
}
```

### Letter Spacing
Adjust spacing between letters (positive to increase, negative to decrease).
```css
p {
  letter-spacing: -0.5em;
}
```

### Word Spacing
Adjust spacing between words.
```css
p {
  word-spacing: 0.25em;
}
```

## Example: Text Properties in Action
```html
<h2><a href="#">I Am a Builder</a></h2>
<p class="byline">Posted by Shay Howe</p>
<p class="intro">Every day I see designers and developers...</p>
```

```css
h2, p {
  color: #555;
  font: 13px/20px "Helvetica Neue", Helvetica, Arial, sans-serif;
}
a {
  color: #0087cc;
}
a:hover {
  color: #ff7b29;
}
h2 {
  font-size: 22px;
  font-weight: bold;
  letter-spacing: -0.02em;
  margin-bottom: 6px;
}
h2 a {
  text-decoration: none;
  text-shadow: 2px 2px 1px rgba(0, 0, 0, 0.2);
}
.byline {
  color: #9799a7;
  font-family: Georgia, Times, "Times New Roman", serif;
  font-style: italic;
  margin-bottom: 18px;
}
.intro {
  text-indent: 15px;
}
.intro a {
  font-size: 11px;
  font-weight: bold;
  text-decoration: underline;
  text-transform: uppercase;
}
```

## Web-Safe Fonts
Commonly available fonts include: Arial, Courier New, Garamond, Georgia, Lucida Sans, Palatino Linotype, Tahoma, Times New Roman, Trebuchet, Verdana.

## Embedding Web Fonts
Use `@font-face` to embed custom fonts.
```css
@font-face {
  font-family: "Lobster";
  src: local("Lobster"), url("lobster.woff") format("woff");
}
body {
  font-family: "Lobster", "Comic Sans", cursive;
}
```
- **Sources**: 
  - Adobe Fonts (subscription): https://fonts.adobe.com/
  - Google Fonts (free): https://fonts.google.com/

## Citations and Quotes
### `<cite>`
Reference a creative work, author, or resource.
```html
<p>The book <cite><a href="http://www.amazon.com/Steve-Jobs-Walter-Isaacson/dp/1451648537">Steve Jobs</a></cite> is truly inspirational.</p>
```

### `<q>`
Short inline quotations.
```html
<p>Steve Jobs once said, <q>One home run is much better than two doubles.</q></p>
```

### `<blockquote>`
Longer external quotations.
```html
<blockquote cite="http://money.cnn.com/magazines/fortune/fortune_archive/2000/01/24/272277/index.htm">
  <p>“In most people’s vocabularies, design is a veneer...”</p>
  <p><cite>— Steve Jobs in <a href="http://money.cnn.com/magazines/fortune/fortune_archive/2000/01/24/272277/index.htm">Fortune Magazine</a></cite></p>
</blockquote>
```

## Summary
- **Font-Based Properties**: `font-family`, `font-size`, `font-style`, `font-weight`, `line-height`.
- **Text-Based Properties**: `text-align`, `text-decoration`, `text-indent`, `text-shadow`, `text-transform`, `letter-spacing`, `word-spacing`.
- **Web Fonts**: Embed via `@font-face` or use services like Google Fonts.
- **Citations & Quotes**: Use `<cite>`, `<q>`, and `<blockquote>` for proper markup.
