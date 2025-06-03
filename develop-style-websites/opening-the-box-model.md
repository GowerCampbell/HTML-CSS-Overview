Opening the Box Model
Looking at how elements are displayed on a page and how they are sized.
Block-level any available width, regardless of content. 
Inline-level elements occupy only the width of their content requres nd line up on the same line.

Display
By determining its property.
p {
  display: block;
}
p {
  display: inline;
}
While it'll behave like an bloack line element it will disply inline with other elements on a new line by default
p {
  display: inline-block;
}
Result: Paragraph one. Paragraph two. Paragraph three.

Using none will hide n element and render the pge as if that doesn't exist.
div {
  display: none;
}

Box Model: Every element on a page is a rectangular box.
Determine the size of the box with:
div {
  border: 6px solid #949599;
  height: 100px;
  margin: 20px;
  padding: 20px;
  width: 400px;
}

Width & Height 
Total width: margin-right + border-right + padding-right + width + padding-left + border-left + margin-left
div {
  width: 400px;
}
Total height: margin-top + border-top + padding-top + height + padding-bottom + border-bottom + margin-bottom
div {
  height: 100px;
}

margin (space round) - border - padding(space inside)

Margin & Padding Declarations



