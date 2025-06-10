
# Creating Lists Guide for Web Design

## List Types
HTML supports three main list types:
- **Unordered Lists (`<ul>`)**: Items with no specific order, marked by bullets.
- **Ordered Lists (`<ol>`)**: Items in a sequence, marked by numbers or letters.
- **Description Lists (`<dl>`)**: Terms with corresponding descriptions.

## Unordered Lists
Display items with a bullet (solid dot by default).
```html
<ul>
  <li>Orange</li>
  <li>Green</li>
  <li>Blue</li>
</ul>
```
- Browsers add vertical margin and left padding by default.

## Ordered Lists
Display items in a sequence, numbered by default.
```html
<ol>
  <li>Head north on N Halsted St</li>
  <li>Turn right on W Diversey Pkwy</li>
  <li>Turn left on N Orchard St</li>
</ol>
```

### Start Attribute
Set the starting number for an ordered list (default is 1).
```html
<ol start="30">
  <li>Head north on N Halsted St</li>
  <li>Turn right on W Diversey Pkwy</li>
  <li>Turn left on N Orchard St</li>
</ol>
```

### Reversed Attribute
Reverse the order of the list (boolean attribute, no value needed).
```html
<ol reversed>
  <li>Head north on N Halsted St</li>
  <li>Turn right on W Diversey Pkwy</li>
  <li>Turn left on N Orchard St</li>
</ol>
```

### Value Attribute
Change the value of a specific list item, affecting subsequent items.
```html
<ol>
  <li>Head north on N Halsted St</li>
  <li value="9">Turn right on W Diversey Pkwy</li>
  <li>Turn left on N Orchard St</li>
</ol>
```

## Description Lists
Pair terms (`<dt>`) with descriptions (`<dd>`). A term can have multiple descriptions.
```html
<dl>
  <dt>study</dt>
  <dd>The devotion of time and attention to acquiring knowledge...</dd>
  <dt>design</dt>
  <dd>A plan or drawing produced to show the look and function...</dd>
  <dd>Purpose, planning, or intention that exists...</dd>
  <dt>business</dt>
  <dt>work</dt>
  <dd>A person's regular occupation, profession, or trade</dd>
</dl>
```
- `<dd>`: Left margin by default.
- `<dl>`: Vertical margins by default.

## Nesting Lists
Lists can be nested within `<li>` elements for semantic structure.
```html
<ol>
  <li>Walk the dog</li>
  <li>Fold laundry</li>
  <li>
    Go to the grocery and buy:
    <ul>
      <li>Milk</li>
      <li>Bread</li>
      <li>Cheese</li>
    </ul>
  </li>
  <li>Mow the lawn</li>
  <li>Make dinner</li>
</ol>
```

## List Item Styling
### List Style Type
Customize markers for `<ul>` and `<ol>` using `list-style-type`.
```css
ul {
  list-style-type: square;
}
```
Available values:
- `none`: No marker.
- `disc`: Filled circle (default for `<ul>`).
- `circle`: Hollow circle.
- `square`: Filled square.
- `decimal`: Numbers (default for `<ol>`).
- `decimal-leading-zero`: Numbers with leading zeros.
- `lower-roman`: Lowercase Roman numerals.
- `upper-roman`: Uppercase Roman numerals.
- `lower-greek`: Lowercase Greek letters.
- `lower-alpha`/`lower-latin`: Lowercase letters.
- `upper-alpha`/`upper-latin`: Uppercase letters.
- `armenian`: Armenian numbering.
- `georgian`: Georgian numbering.

### Using an Image as a Marker
Replace default markers with an image.
```css
li {
  background: url("arrow.png") 0 50% no-repeat;
  list-style-type: none;
  padding-left: 12px;
}
```

### List Style Position
Control marker placement with `list-style-position`.
```css
ul {
  list-style-position: inside;
}
```
- `outside` (default): Marker outside the `<li>` content.
- `inside`: Marker inline with the first line, content wraps below.
- `inherit`: Inherits from parent.

### Shorthand List Style
Combine `list-style-type` and `list-style-position`.
```css
ul {
  list-style: circle inside;
}
ol {
  list-style: lower-roman;
}
```

## Horizontally Displaying Lists
Display list items in a row using `display` or `float`.

### Display Inline or Inline-Block
```html
<ul>
  <li>Orange</li>
  <li>Green</li>
  <li>Blue</li>
</ul>
```
```css
li {
  display: inline-block;
  margin: 0 10px;
}
```

### Floating Lists
```css
li {
  float: left;
  margin: 0 20px;
}
```
- Use margins or padding to prevent marker overlap.
- Apply clearfix to restore normal flow.

## Navigational List Example
Create a horizontal navigation menu.
```html
<nav class="navigation">
  <ul>
    <li><a href="#">Profile</a></li><!--
    --><li><a href="#">Settings</a></li><!--
    --><li><a href="#">Notifications</a></li><!--
    --><li><a href="#">Logout</a></li>
  </ul>
</nav>
```
```css
.navigation ul {
  font: bold 11px "Helvetica Neue", Helvetica, Arial, sans-serif;
  margin: 0;
  padding: 0;
  text-transform: uppercase;
}
.navigation li {
  display: inline-block;
}
.navigation a {
  background: linear-gradient(#49708f, #293f50);
  border-right: 1px solid rgba(0, 0, 0, 0.3);
  color: #fff;
  padding: 12px 20px;
  text-decoration: none;
}
.navigation a:hover {
  background: #314b60;
  box-shadow: inset 0 0 10px 1px rgba(0, 0, 0, 0.3);
}
.navigation li:first-child a {
  border-radius: 4px 0 0 4px;
}
.navigation li:last-child a {
  border-right: 0;
  border-radius: 0 4px 4px 0;
}
```

## Summary
- **List Types**: Unordered (`<ul>`), ordered (`<ol>`), and description (`<dl>`) lists.
- **Attributes**: `start`, `reversed`, and `value` for ordered lists.
- **Nesting**: Embed lists within `<li>` for semantic structure.
- **Styling**: Customize markers with `list-style-type`, images, or `list-style-position`.
- **Horizontal Lists**: Use `display: inline-block` or `float: left` for navigation or row layouts.
