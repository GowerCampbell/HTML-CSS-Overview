
# Getting to Know CSS

**Note**: CSS is not made from JavaScript; it is a separate language used to style HTML elements. The order and specificity of selectors determine how styles are applied to a website.

## The Cascade
The cascade determines which styles are applied when multiple rules target the same element. Later rules override earlier ones for the same property.

```css
p {
  background: orange;
  font-size: 24px;
}
p {
  background: green;
}
```
The background will be `green` because the later rule overrides the earlier one for the same property.

## Calculating Specificity
Every selector has a weight that determines its precedence. Specificity is calculated using a three-part value: **(ID, Class, Type)**.
- **ID selectors**: `1-0-0` (highest specificity).
- **Class selectors**: `0-1-0`.
- **Type selectors**: `0-0-1` (lowest specificity).

Example:
```html
<p id="food">...</p>
```
```css
#food {
  background: green;
}
p {
  background: orange;
}
```
The `#food` selector (`1-0-0`) overrides the `p` selector (`0-0-1`), so the background will be `green`.

## Combining Selectors
Selectors can be combined to target specific elements with shared properties.

```html
<div class="hotdog">
  <p>...</p>
  <p>...</p>
  <p class="mustard">...</p>
</div>
```

### Read Right to Left
CSS selectors are read from right to left. The rightmost selector is the **key selector**, while those to the left are **prequalifiers**.

```css
.hotdog p {
  background: brown;
}
.hotdog p.mustard {
  background: yellow;
}
```
- `.hotdog p`: Targets all `<p>` elements inside an element with class `hotdog`.
- `.hotdog p.mustard`: Targets `<p>` elements with class `mustard` inside an element with class `hotdog`.

### Spaces Within Selectors
Spaces indicate a descendant relationship. For example, `.hotdog p.mustard` only selects `<p>` elements with the `mustard` class inside a `.hotdog` element.

### Specificity Within Combined Selectors
Specificity is cumulative. The selector with the higher total weight wins.

```css
.hotdog p.mustard {
  background: yellow; /* Specificity: 0-2-1 (1 class + 1 class + 1 type) */
}
.hotdog p {
  background: brown; /* Specificity: 0-1-1 (1 class + 1 type) */
}
```
The `.hotdog p.mustard` rule applies due to higher specificity.

## Layering Styles with Multiple Classes
Elements can have multiple classes (space-separated) to reuse styles without increasing specificity.

```html
<a class="btn btn-danger">...</a>
<a class="btn btn-success">...</a>
```

```css
.btn {
  font-size: 16px;
}
.btn-danger {
  background: red;
}
.btn-success {
  background: green;
}
```
The `.btn` class applies shared styles, while `.btn-danger` and `.btn-success` add specific styles.

## Common CSS Property Values

### Colors
Colors can be defined in multiple formats, all based on the sRGB color space.

#### RGB Colors
```css
.task {
  background: rgb(128, 0, 0);
}
.count {
  background: rgb(255, 255, 0);
}
```

#### Keyword Colors
```css
.task {
  background: maroon;
}
.count {
  background: yellow;
}
```

#### Hexadecimal Colors
Shortened (e.g., `#f60`) or full (e.g., `#ff6600`) formats.
```css
.task {
  background: #800000;
}
.count {
  background: #ff0;
}
```

#### HSL & HSLa Colors
HSL uses hue, saturation, and lightness. HSLa adds an alpha channel for opacity (0–1).
```css
.task {
  background: hsl(0, 100%, 25%);
}
.count {
  background: hsl(60, 100%, 50%);
}
.task {
  background: hsla(0, 100%, 25%, 0.25); /* 25% opacity */
}
.count {
  background: hsla(60, 100%, 50%, 1); /* Fully opaque */
}
```

### Length Values
Length values can be **absolute** (fixed) or **relative** (context-dependent).

#### Absolute Lengths
Fixed measurements, such as pixels (`px`), where 1px = 1/96th of an inch.
```css
p {
  font-size: 14px;
}
```

#### Relative Lengths
Calculated based on context.

##### Percentages
Relative to the parent element’s size.
```css
.col {
  width: 50%; /* 50% of parent’s width */
}
```

##### Em
Relative to the element’s font size.
```css
.banner {
  font-size: 14px;
  width: 5em; /* 5 × 14px = 70px */
}
```








