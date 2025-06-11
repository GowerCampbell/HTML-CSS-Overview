
# Organizing Data with Tables Guide

Tables in HTML are used to display structured tabular data in a readable format, suitable for data like schedules, inventories, or comparisons. They can also be used for layout, though CSS is preferred for positioning.

## Creating a Table
Tables are built using specific HTML elements to structure data:
- `<table>`: Initializes the table.
- `<tr>`: Defines a table row.
- `<td>`: Defines table data (cells).
- `<th>`: Defines table headers for semantic clarity.

### Table (`<table>`)
Wraps the entire table.
```html
<table>
  ...
</table>
```

### Table Row (`<tr>`)
Defines rows within the table.
```html
<table>
  <tr>
    ...
  </tr>
  <tr>
    ...
  </tr>
</table>
```

### Table Data (`<td>`)
Creates cells within a row, forming columns.
```html
<table>
  <tr>
    <td>Don’t Make Me Think by Steve Krug</td>
    <td>In Stock</td>
    <td>1</td>
    <td>$30.02</td>
  </tr>
  ...
</table>
```

### Table Header (`<th>`)
Identifies header cells, with a `scope` attribute (`col`, `row`, `colgroup`, `rowgroup`) to indicate what they describe.
```html
<table>
  <tr>
    <th scope="col">Item</th>
    <th scope="col">Availability</th>
    <th scope="col">Qty</th>
    <th scope="col">Price</th>
  </tr>
  <tr>
    <td>Don’t Make Me Think by Steve Krug</td>
    <td>In Stock</td>
    <td>1</td>
    <td>$30.02</td>
  </tr>
  ...
</table>
```

## Table Structure
### Table Caption
The `<caption>` element provides a title for the table.
```html
<table>
  <caption>Design and Front-End Development Books</caption>
  ...
</table>
```

### Table Head, Body, and Foot
Organize content with `<thead>`, `<tbody>`, and `<tfoot>`:
- `<thead>`: Contains header rows.
- `<tbody>`: Holds primary data.
- `<tfoot>`: Summarizes data (e.g., totals).
```html
<table>
  <caption>Design and Front-End Development Books</caption>
  <thead>
    <tr>
      <th scope="col">Item</th>
      <th scope="col">Availability</th>
      <th scope="col">Qty</th>
      <th scope="col">Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Don’t Make Me Think by Steve Krug</td>
      <td>In Stock</td>
      <td>1</td>
      <td>$30.02</td>
    </tr>
    ...
  </tbody>
  <tfoot>
    <tr>
      <td colspan="3">Subtotal</td>
      <td>$135.36</td>
    </tr>
    <tr>
      <td colspan="3">Tax</td>
      <td>$13.54</td>
    </tr>
    <tr>
      <td colspan="3">Total</td>
      <td>$148.90</td>
    </tr>
  </tfoot>
</table>
```

### Combining Multiple Cells
Use `colspan` and `rowspan` to merge cells:
- `colspan`: Spans a cell across multiple columns.
- `rowspan`: Spans a cell across multiple rows.
```html
<tr>
  <th scope="col" colspan="2">Item</th>
  <th scope="col">Qty</th>
  <th scope="col">Price</th>
</tr>
```

## Table Borders
### Border Collapse Property
Controls how borders are rendered:
- `collapse`: Merges adjacent borders into one.
- `separate` (default): Keeps borders distinct.
- `inherit`: Inherits from parent.
```css
table {
  border-collapse: collapse;
}
th, td {
  border: 1px solid #cecfd5;
  padding: 10px 15px;
}
```

### Border Spacing Property
Sets spacing between cell borders when `border-collapse` is `separate`. Accepts one value (uniform spacing) or two (horizontal, vertical).
```css
table {
  border-collapse: separate;
  border-spacing: 4px;
}
table, th, td {
  border: 1px solid #cecfd5;
}
th, td {
  padding: 10px 15px;
}
```

### Borders on Rows
Borders cannot be applied directly to `<tr>` or structural elements. Use `border-bottom` on `<th>` or `<td>`, and remove unwanted borders with `:last-child`.
```css
table {
  border-collapse: collapse;
}
th, td {
  border-bottom: 1px solid #cecfd5;
  padding: 10px 15px;
}
tfoot tr:last-child td {
  border-bottom: 0;
}
```

## Table Striping
Alternate row backgrounds for readability using `:nth-child`.
```css
tbody tr:nth-child(even) {
  background: #f0f0f2;
}
```

## Aligning Text
Use `text-align` for horizontal alignment and `vertical-align` (`top`, `middle`, `bottom`) for vertical alignment in table cells.
```css
.item-stock, .item-qty {
  text-align: center;
}
.item-price {
  text-align: right;
}
th, td {
  vertical-align: middle;
}
```

## Fully Styled Table Example
```html
<table>
  <thead>
    <tr>
      <th scope="col" colspan="2">Item</th>
      <th scope="col">Qty</th>
      <th scope="col">Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <strong class="book-title">Don’t Make Me Think</strong>
        <span class="text-offset">by Steve Krug</span>
      </td>
      <td class="item-stock">In Stock</td>
      <td class="item-qty">1</td>
      <td class="item-price">$30.02</td>
    </tr>
    <tr>
      <td>
        <strong class="book-title">A Project Guide to UX Design</strong>
        <span class="text-offset">by Russ Unger & Carolyn Chandler</span>
      </td>
      <td class="item-stock">In Stock</td>
      <td class="item-qty">2</td>
      <td class="item-price">$52.94 <span class="text-offset item-multiple">$26.47 × 2</span></td>
    </tr>
    <tr>
      <td>
        <strong class="book-title">Introducing HTML5</strong>
        <span class="text-offset">by Bruce Lawson & Remy Sharp</span>
      </td>
      <td class="item-stock">Out of Stock</td>
      <td class="item-qty">1</td>
      <td class="item-price">$22.23</td>
    </tr>
    <tr>
      <td>
        <strong class="book-title">Bulletproof Web Design</strong>
        <span class="text-offset">by Dan Cederholm</span>
      </td>
      <td class="item-stock">In Stock</td>
      <td class="item-qty">1</td>
      <td class="item-price">$30.17</td>
    </tr>
  </tbody>
  <tfoot>
    <tr class="text-offset">
      <td colspan="3">Subtotal</td>
      <td>$135.36</td>
    </tr>
    <tr class="text-offset">
      <td colspan="3">Tax</td>
      <td>$13.54</td>
    </tr>
    <tr>
      <td colspan="3">Total</td>
      <td>$148.90</td>
    </tr>
  </tfoot>
</table>
```
```css
table {
  border-collapse: separate;
  border-spacing: 0;
  color: #4a4a4d;
  font: 14px/1.4 "Helvetica Neue", Helvetica, Arial, sans-serif;
}
th, td {
  padding: 10px 15px;
  vertical-align: middle;
}
thead {
  background: linear-gradient(#49708f, #293f50);
  color: #fff;
  font-size: 11px;
  text-transform: uppercase;
}
th:first-child {
  border-top-left-radius: 5px;
  text-align: left;
}
th:last-child {
  border-top-right-radius: 5px;
}
tbody tr:nth-child(even) {
  background: #f0f0f2;
}
td {
  border-bottom: 1px solid #cecfd5;
  border-right: 1px solid #cecfd5;
}
td:first-child {
  border-left: 1px solid #cecfd5;
}
.book-title {
  color: #395870;
  display: block;
}
.text-offset {
  color: #7c7c80;
  font-size: 12px;
}
.item-stock, .item-qty {
  text-align: center;
}
.item-price {
  text-align: right;
}
.item-multiple {
  display: block;
}
tfoot {
  text-align: right;
}
tfoot tr:last-child {
  background: #f0f0f2;
  color: #395870;
  font-weight: bold;
}
tfoot tr:last-child td:first-child {
  border-bottom-left-radius: 5px;
}
tfoot tr:last-child td:last-child {
  border-bottom-right-radius: 5px;
}
```

## Summary
- **Core Elements**: Use `<table>`, `<tr>`, `<td>`, and `<th>` to structure tabular data.
- **Semantic Structure**: Enhance with `<caption>`, `<thead>`, `<tbody>`, and `<tfoot>`.
- **Merging Cells**: Use `colspan` and `rowspan` for layout flexibility.
- **Borders**: Control with `border-collapse` and `border-spacing`; style borders on `<th>` and `<td>`.
- **Styling**: Apply striping with `:nth-child`, and align text with `text-align` and `vertical-align`.
