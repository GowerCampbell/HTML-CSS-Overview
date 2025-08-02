

# Complex Selectors in CSS

Complex selectors are essential tools in CSS that allow you to target elements with precision. They shape the cascade by increasing the **specificity** of a rule, making it more likely to be applied over more general rules. By combining selectors, you can target elements based on their type, attributes, state (like being hovered over or checked), and position within the document structure (like being the first or last child).

## Complex Selectors Overview

<details>
<summary>How are complex selectors used to shape the cascade and determine which styles are applied?</summary>
<p>They are used to increase the specificity of a CSS rule. The browser's rendering engine follows a set of rules, known as the cascade, to determine which style to apply to an element when multiple rules conflict. A more specific selector (e.g., `#nav .link`) will override a less specific one (e.g., `a`). This allows for fine-grained control over the appearance of elements on a page.</p>
</details>

<details>
<summary>How can you select different types of elements and elements in different states?</summary>
<p>CSS provides a wide range of selectors for this purpose. You can use <b>Type Selectors</b> (`p`, `div`) for element types, <b>Class Selectors</b> (`.button`) for groups of elements, and <b>ID Selectors</b> (`#header`) for unique elements. For different states, you can use <b>Pseudo-classes</b> like `:hover` (when a mouse is over an element), `:focus` (when an element is selected), or `:checked` (for checkboxes and radio buttons).</p>
</details>

CSS3 has brought new selectors, opening a new world of opportunities and improvements to existing practices beyond the base ID, class, and descendant selectors.

## Basic Selectors

<details>
<summary>1. Universal Selector (`*`)</summary>
<p>The universal selector targets every single element on the page. It's often used to reset default browser styles.</p>

```css
* {
  margin: 0;
  padding: 0;
}
```

<p>It can also be used with child selectors to target every element that is a child of another element:</p>

```css
#container * {
  border: 1px solid black;
}
```

</details>

<details>
<summary>2. ID Selector (`#`)</summary>
<p>The ID selector is used to identify and select a unique element based on its `id` attribute value. An ID should only be used once per page.</p>

```css
#container {
  width: 960px;
  margin: auto;
}
```

</details>

<details>
<summary>3. Class Selector (`.`)</summary>
<p>The class selector applies styles to multiple elements based on their `class` attribute value. A class can be reused on many elements.</p>

```css
.error {
  color: red;
}
```

</details>

<details>
<summary>4. Type Selector</summary>
<p>The type selector targets elements using their HTML tag name.</p>

```css
a { color: red; }
ul { margin-left: 0; }
```

</details>

## Combinator Selectors

<details>
<summary>5. Descendant Selector (` `)</summary>
<p>The descendant selector (a space) targets elements that are children or descendants of a specified parent element. They do not have to be direct children.</p>

```css
li a {
  text-decoration: none;
}
```

<p>For example, `article h2` will select all `<h2>` elements inside an `<article>`, no matter how deeply nested.</p>

```html
<article>
  <h2>This heading will be selected</h2>
  <div>
    <h2>This heading will be selected</h2>
  </div>
</article>
```

</details>

<details>
<summary>6. Adjacent Sibling Selector (`+`)</summary>
<p>The adjacent sibling selector (`+`) selects an element that directly follows another element at the same hierarchy level (i.e., they share the same parent).</p>

```css
ul + p {
  color: red;
}
```

<p>This will select the first `<p>` element that immediately comes after a `<ul>`.</p>

```html
<ul>...</ul>
<p>This paragraph text turns red.</p>
```

</details>

<details>
<summary>7. Direct Child Selector (`>`)</summary>
<p>The direct child selector (`>`), or child combinator, selects only the direct children of a parent element.</p>

```css
div#container > ul {
  border: 1px solid black;
}
```

<p>This styles only the `<ul>` that is a direct child of `#container`, preventing the style from affecting nested lists.</p>

```html
<div id="container">
  <ul> <li> List Item
      <ul> <li> Child </li>
      </ul>
    </li>
    <li> List Item </li>
  </ul>
</div>
```

</details>

<details>
<summary>8. General Sibling Selector (`~`)</summary>
<p>The general sibling selector (`~`) selects all elements that are siblings of a specified element and come after it, sharing the same parent.</p>

```css
ul ~ p {
  color: red;
}
```

<p>This targets any `<p>` elements that follow a `<ul>` and share the same parent.</p>
</details>

## Attribute Selectors

<details>
<summary>9. Attribute Presence Selector (`[attr]`)</summary>
<p>This selects an element if it has the specified attribute, regardless of the attribute's value.</p>

```css
a[target] {
  color: green;
}
```

<p>This selects only anchor tags that have a `target` attribute.</p>

```html
<a href="#" target="_blank">This link will be green.</a>
<a href="#">This link will not.</a>
```

</details>

<details>
<summary>10. Attribute Equals Selector (`[attr="value"]`)</summary>
<p>This provides an exact match for an attribute's value.</p>

```css
a[href="http://google.com/"] {
  color: #83b348;
}
```

<p>This will style only the anchor tag whose `href` attribute is exactly "http://google.com/".</p>
</details>

<details>
<summary>11. Attribute Contains Selector (`[attr*="value"]`)</summary>
<p>This selects an element if the attribute value contains the specified substring. The asterisk (`*`) designates that the value must appear somewhere in the attribute's value.</p>

```css
a[href*="tutsplus"] {
  color: #83b348;
}
```

</details>

<details>
<summary>12. Attribute Begins With Selector (`[attr^="value"]`)</summary>
<p>Using a circumflex accent (`^`), this selects an element whose attribute value begins with the specified string. This is useful for things like styling all external links.</p>

```css
a[href^="https"] {
  background: url(path/to/external/icon.png) no-repeat;
  padding-left: 10px;
}
```

</details>

<details>
<summary>13. Attribute Ends With Selector (`[attr$="value"]`)</summary>
<p>Using a dollar sign (`$`), this selects an element whose attribute value ends with the specified string. This is useful for styling links based on file type.</p>

```css
a[href$=".jpg"] {
  color: red;
}
```

</details>

<details>
<summary>14. Attribute for Data Consolidation (`[data-*]`)</summary>
<p>Instead of creating multiple selectors for different file types, you can use a custom `data-*` attribute to group them.</p>

<p>Instead of this:</p>

```css
a[href$=".jpg"],
a[href$=".jpeg"],
a[href$=".png"],
a[href$=".gif"],
a[href$=".webp"] {
  color: red;
}
```

<p>You can use this HTML:</p>

```html
<a href="path/to/image.jpg" data-filetype="image"> Image Link </a>
```

<p>And target it with this simpler CSS:</p>

```css
a[data-filetype="image"] {
  color: red;
}
```

</details>

<details>
<summary>15. Attribute Spaced Selector (`[attr~="value"]`)</summary>
<p>The tilde (`~`) allows you to target an attribute that has a space-separated list of values, matching when one of the words is the specified value.</p>

```html
<a href="path/to/image.jpg" data-info="external image"> Click Me, Fool </a>
```

```css
a[data-info~="external"] {
  color: red;
}
a[data-info~="image"] {
  border: 1px solid black;
}
```

</details>

<details>
<summary>16. Attribute Hyphenated Selector (`[attr|="value"]`)</summary>
<p>The vertical line (`|`) targets attributes that have a hyphen-separated list of values, where the value starts with the specified string.</p>

```css
a[lang|="en"] { ... }
```

<p>This will match the following element:</p>

```html
<a href="#" lang="en-US">...</a>
```

</details>

## Pseudo-class Selectors

<details>
<summary>17. Link Pseudo-classes (`:link`, `:visited`)</summary>
<ul>
<li>`:link` targets anchor tags that have not yet been clicked.</li>
<li>`:visited` targets anchor tags that have already been clicked.</li>
</ul>

```css
a:link { color: red; }
a:visited { color: purple; }
```

</details>

<details>
<summary>18. User Action Pseudo-classes (`:hover`, `:active`, `:focus`)</summary>
<ul>
<li>`:hover` applies when the mouse cursor is over an element.</li>
<li>`:active` applies when a user clicks or engages an element.</li>
<li>`:focus` applies when an element has focus (e.g., a form input).</li>
</ul>

```css
div:hover {
  background: #e3e3e3;
}

a:active {
  color: orange;
}

input:focus {
  border-color: blue;
}
```

</details>

<details>
<summary>19. UI State Pseudo-classes (`:enabled`, `:disabled`, `:checked`)</summary>
<p>These pseudo-classes target elements based on their current state in the user interface.</p>
<ul>
<li>`:enabled` / `:disabled`: Targets form elements that are available or unavailable for interaction.</li>
<li>`:checked`: Targets radio buttons or checkboxes that are selected.</li>
</ul>

```css
input[type=radio]:checked {
  border: 1px solid black;
}

input:disabled {
  background-color: #ccc;
}
```

</details>

<details>
<summary>20. Target Pseudo-class (`:target`)</summary>
<p>Used to style an element whose `id` attribute matches a URI fragment. For example, if the URL is `http://example.com/index.html#hello`, the `:target` pseudo-class will match the element with `id="hello"`.</p>

```html
<section id="hello">...</section>
```

```css
section:target {
  background-color: yellow;
}
```

</details>

<details>
<summary>21. Empty Pseudo-class (`:empty`)</summary>
<p>Selects elements that do not contain any children or text nodes. Whitespace, comments, and processing instructions are not considered children for this purpose.</p>

```css
div:empty {
  border: 1px solid red;
}
```

```html
<div>Hello</div>
<div></div>
<div></div><div> </div> <div><strong></strong></div>
```

</details>

<details>
<summary>22. Negation Pseudo-class (`:not()`)</summary>
<p>The `:not(x)` pseudo-class takes an argument (a selector) and selects elements that do <em>not</em> match that argument.</p>

```css
div:not(#container) {
  color: blue;
}
```

<p>This selects all `<div>` elements except for the one with the ID of `container`.</p>
</details>

## Pseudo-element Selectors (`::`)

*Note: The double colon `::` syntax is used to distinguish pseudo-elements from pseudo-classes. Modern browsers support both `::` and the older single colon `:` syntax for backward compatibility with CSS2 pseudo-elements (`:before`, `:after`, etc.), but `::` is the current standard.*

<details>
<summary>23. Textual Pseudo-elements (`::first-line`, `::first-letter`)</summary>
<ul>
<li>`::first-line`: Targets the first line of a block-level element.</li>
<li>`::first-letter`: Targets the first letter of a block-level element.</li>
</ul>

```css
p::first-line {
  font-weight: bold;
  font-size: 1.2em;
}

p::first-letter {
  float: left;
  font-size: 2em;
  font-weight: bold;
  padding-right: 2px;
}
```

</details>

<details>
<summary>24. Generated Content Pseudo-elements (`::before`, `::after`)</summary>
<p>These create a new inline-level pseudo-element just inside the selected element, either before or after its content. They are used in conjunction with the `content` property.</p>

```css
p::after {
  content: " ∎"; /* Adds a square at the end of every paragraph */
  display: inline;
}
```

</details>

<details>
<summary>25. Fragment Pseudo-element (`::selection`)</summary>
<p>This pseudo-element applies styles to the part of a document that has been highlighted by the user (e.g., by clicking and dragging the mouse). Only a few properties can be used: `color`, `background`, `background-color`, and `text-shadow`.</p>
<p>For cross-browser compatibility, you should include vendor prefixes.</p>

```css
::-moz-selection {
  background: #ff7b29;
}
::selection {
  background: #ff7b29;
}
```

</details>

## Structural & Positional Pseudo-classes

<details>
<summary>26. Nth Child Selectors (`:nth-child(n)`, `:nth-last-child(n)`)</summary>
<p>These selectors target elements based on their position among a group of siblings.</p>
<ul>
<li>`:nth-child(n)` counts from the beginning.</li>
<li>`:nth-last-child(n)` counts from the end.</li>
</ul>
<p>The argument `n` can be an integer, a keyword (`odd`, `even`), or a formula (`an+b`).</p>
<p><b>Select the 3rd `<li>`:</b></p>

```css
li:nth-child(3) {
  color: red;
}
```

<p><b>Select every second item starting from the 3rd:</b></p>

```css
li:nth-child(2n+3) { ... }
```

<p><b>Select the first 4 items:</b></p>

```css
li:nth-child(-n+4) { ... }
```

</details>

<details>
<summary>27. Nth of Type Selectors (`:nth-of-type(n)`, `:nth-last-of-type(n)`)</summary>
<p>This works similarly to `:nth-child`, but it only considers elements of the same type. This is useful when you have mixed element types within a parent.</p>
<p><b>Select the 3rd `<p>` element inside its parent:</b></p>

```css
p:nth-of-type(3) {
  color: red;
}
```

<p><b>Select every odd paragraph, counting from the end:</b></p>

```css
p:nth-last-of-type(2n+1) {
  border: 1px solid black;
}
```

</details>

<details>
<summary>28. First, Last, and Only Child Selectors</summary>
<ul>
<li>`:first-child`: Selects an element that is the first child of its parent.</li>
<li>`:last-child`: Selects an element that is the last child of its parent.</li>
<li>`:only-child`: Selects an element that is the only child of its parent.</li>
</ul>

```css
/* Remove top border from the very first list item */
ul li:first-child {
  border-top: none;
}

/* Target a paragraph only if it's the only element inside its parent div */
div p:only-child {
  color: red;
}
```

</details>

<details>
<summary>29. First, Last, and Only of Type Selectors</summary>
<ul>
<li>`:first-of-type`: Selects the first element of its type within its parent.</li>
<li>`:last-of-type`: Selects the last element of its type within its parent.</li>
<li>`:only-of-type`: Selects an element that is the only one of its type within its parent.</li>
</ul>

```css
/* Make the text bold if a list item is the only one of its kind (e.g., a ul with only one li) */
ul > li:only-of-type {
  font-weight: bold;
}
```

</details>

<details>
<summary>30. Combining Selectors: A Challenge</summary>
<p>Given the following HTML, how would you target only the second list item ("List Item 2")?</p>

```html
<div>
  <p> My paragraph here. </p>
  <ul>
    <li> List Item 1 </li>
    <li> List Item 2 </li>
  </ul>
  <ul>
    <li> List Item 3 </li>
    <li> List Item 4 </li>
  </ul>   
</div>
```

<p><b>Solution 1:</b> Target the first `<ul>` of its type, then find its second `<li>` child.</p>

```css
ul:first-of-type > li:nth-child(2) {
  font-weight: bold;
}
```

<p><b>Solution 2:</b> Use the adjacent sibling selector to find the `<ul>` after the `<p>`, then find its last child.</p>

```css
p + ul li:last-child {
  font-weight: bold;
}
```

<p><b>Solution 3:</b> Target the first `<ul>` of its type, then find the first `<li>` from the end (which is the second item).</p>

```css
ul:first-of-type li:nth-last-child(1) {
  font-weight: bold;
}
```

</details>

\<p\>The universal selector targets every single element on the page. It's often used to reset default browser styles.\</p\>

```css
* {
  margin: 0;
  padding: 0;
}
```

\<p\>It can also be used with child selectors to target every element that is a child of another element:\</p\>

```css
#container * {
  border: 1px solid black;
}
```

\</details\>

\<details\>
\<summary\>2. ID Selector (\<code\>\#\</code\>)\</summary\>
\<p\>The ID selector is used to identify and select a unique element based on its \<code\>id\</code\> attribute value. An ID should only be used once per page.\</p\>

```css
#container {
  width: 960px;
  margin: auto;
}
```

\</details\>

\<details\>
\<summary\>3. Class Selector (\<code\>.\</code\>)\</summary\>
\<p\>The class selector applies styles to multiple elements based on their \<code\>class\</code\> attribute value. A class can be reused on many elements.\</p\>

```css
.error {
  color: red;
}
```

\</details\>

\<details\>
\<summary\>4. Type Selector\</summary\>
\<p\>The type selector targets elements using their HTML tag name.\</p\>

```css
a { color: red; }
ul { margin-left: 0; }
```

\</details\>

-----

## Combinator Selectors

\<details\>
\<summary\>5. Descendant Selector (\<code\> \</code\>)\</summary\>
\<p\>The descendant selector (a space) targets elements that are children or descendants of a specified parent element. They do not have to be direct children.\</p\>

```css
li a {
  text-decoration: none;
}
```

\<p\>For example, \<code\>article h2\</code\> will select all \<code\>\&lt;h2\&gt;\</code\> elements inside an \<code\>\&lt;article\&gt;\</code\>, no matter how deeply nested.\</p\>

```html
<article>
  <h2>This heading will be selected</h2>
  <div>
    <h2>This heading will be selected</h2>
  </div>
</article>
```

\</details\>

\<details\>
\<summary\>6. Adjacent Sibling Selector (\<code\>+\</code\>)\</summary\>
\<p\>The adjacent sibling selector (\<code\>+\</code\>) selects an element that directly follows another element at the same hierarchy level (i.e., they share the same parent).\</p\>

```css
ul + p {
  color: red;
}
```

\<p\>This will select the first \<code\>\&lt;p\&gt;\</code\> element that immediately comes after a \<code\>\&lt;ul\&gt;\</code\>.\</p\>

```html
<ul>...</ul>
<p>This paragraph text turns red.</p>
```

\</details\>

\<details\>
\<summary\>7. Direct Child Selector (\<code\>\>\</code\>)\</summary\>
\<p\>The direct child selector (\<code\>\>\</code\>), or child combinator, selects only the direct children of a parent element.\</p\>

```css
div#container > ul {
  border: 1px solid black;
}
```

\<p\>This styles only the \<code\>\&lt;ul\&gt;\</code\> that is a direct child of \<code\>\#container\</code\>, preventing the style from affecting nested lists.\</p\>

```html
<div id="container">
  <ul> <li> List Item
      <ul> <li> Child </li>
      </ul>
    </li>
    <li> List Item </li>
  </ul>
</div>
```

\</details\>

\<details\>
\<summary\>8. General Sibling Selector (\<code\>\~\</code\>)\</summary\>
\<p\>The general sibling selector (\<code\>\~\</code\>) selects all elements that are siblings of a specified element and come after it, sharing the same parent.\</p\>

```css
ul ~ p {
  color: red;
}
```

\<p\>This targets any \<code\>\&lt;p\&gt;\</code\> elements that follow a \<code\>\&lt;ul\&gt;\</code\> and share the same parent.\</p\>
\</details\>

-----

## Attribute Selectors

\<details\>
\<summary\>9. Attribute Presence Selector (\<code\>[attr]\</code\>)\</summary\>
\<p\>This selects an element if it has the specified attribute, regardless of the attribute's value.\</p\>

```css
a[target] {
  color: green;
}
```

\<p\>This selects only anchor tags that have a \<code\>target\</code\> attribute.\</p\>

```html
<a href="#" target="_blank">This link will be green.</a>
<a href="#">This link will not.</a>
```

\</details\>

\<details\>
\<summary\>10. Attribute Equals Selector (\<code\>[attr="value"]\</code\>)\</summary\>
\<p\>This provides an exact match for an attribute's value.\</p\>

```css
a[href="http://google.com/"] {
  color: #83b348;
}
```

\<p\>This will style only the anchor tag whose \<code\>href\</code\> attribute is exactly "[http://google.com/](http://google.com/)".\</p\>
\</details\>

\<details\>
\<summary\>11. Attribute Contains Selector (\<code\>[attr\*="value"]\</code\>)\</summary\>
\<p\>This selects an element if the attribute value contains the specified substring. The asterisk (\<code\>\*\</code\>) designates that the value must appear somewhere in the attribute's value.\</p\>

```css
a[href*="tutsplus"] {
  color: #83b348;
}
```

\</details\>

\<details\>
\<summary\>12. Attribute Begins With Selector (\<code\>[attr^="value"]\</code\>)\</summary\>
\<p\>Using a circumflex accent (\<code\>^\</code\>), this selects an element whose attribute value begins with the specified string. This is useful for things like styling all external links.\</p\>

```css
a[href^="https"] {
  background: url(path/to/external/icon.png) no-repeat;
  padding-left: 10px;
}
```

\</details\>

\<details\>
\<summary\>13. Attribute Ends With Selector (\<code\>[attr$="value"]\</code\>)\</summary\>
\<p\>Using a dollar sign (\<code\>$\</code\>), this selects an element whose attribute value ends with the specified string. This is useful for styling links based on file type.\</p\>

```css
a[href$=".jpg"] {
  color: red;
}
```

\</details\>

\<details\>
\<summary\>14. Attribute for Data Consolidation (\<code\>[data-*]\</code\>)\</summary\>
\<p\>Instead of creating multiple selectors for different file types, you can use a custom \<code\>data-*\</code\> attribute to group them.\</p\>

\<p\>Instead of this:\</p\>

```css
a[href$=&quot;.jpg&quot;],
a[href$=&quot;.jpeg&quot;],
a[href$=&quot;.png&quot;],
a[href$=&quot;.gif&quot;],
a[href$=&quot;.webp&quot;] {
  color: red;
}
```

\<p\>You can use this HTML:\</p\>

```html
&lt;a href=&quot;path/to/image.jpg&quot; data-filetype=&quot;image&quot;&gt; Image Link &lt;/a&gt;
```

\<p\>And target it with this simpler CSS:\</p\>

```css
a[data-filetype=&quot;image&quot;] {
  color: red;
}
```

\</details\>

\<details\>
\<summary\>15. Attribute Spaced Selector (\<code\>[attr\~="value"]\</code\>)\</summary\>
\<p\>The tilde (\<code\>\~\</code\>) allows you to target an attribute that has a space-separated list of values, matching when one of the words is the specified value.\</p\>

```html
<a href="path/to/image.jpg" data-info="external image"> Click Me, Fool </a>
```

```css
a[data-info~="external"] {
  color: red;
}
a[data-info~="image"] {
  border: 1px solid black;
}
```

\</details\>

\<details\>
\<summary\>16. Attribute Hyphenated Selector (\<code\>[attr|="value"]\</code\>)\</summary\>
\<p\>The vertical line (\<code\>|\</code\>) targets attributes that have a hyphen-separated list of values, where the value starts with the specified string.\</p\>

```css
a[lang|="en"] { ... }
```

\<p\>This will match the following element:\</p\>

```html
&lt;a href=&quot;#&quot; lang=&quot;en-US&quot;&gt;...&lt;/a&gt;
```

\</details\>

-----

## Pseudo-class Selectors

\<details\>
\<summary\>17. Link Pseudo-classes (\<code\>:link\</code\>, \<code\>:visited\</code\>)\</summary\>
\<ul\>
\<li\>\<code\>:link\</code\> targets anchor tags that have not yet been clicked.\</li\>
\<li\>\<code\>:visited\</code\> targets anchor tags that have already been clicked.\</li\>
\</ul\>

```css
a:link { color: red; }
a:visited { color: purple; }
```

\</details\>

\<details\>
\<summary\>18. User Action Pseudo-classes (\<code\>:hover\</code\>, \<code\>:active\</code\>, \<code\>:focus\</code\>)\</summary\>
\<ul\>
\<li\>\<code\>:hover\</code\> applies when the mouse cursor is over an element.\</li\>
\<li\>\<code\>:active\</code\> applies when a user clicks or engages an element.\</li\>
\<li\>\<code\>:focus\</code\> applies when an element has focus (e.g., a form input).\</li\>
\</ul\>

```css
div:hover {
  background: #e3e3e3;
}

a:active {
  color: orange;
}

input:focus {
  border-color: blue;
}
```

\</details\>

\<details\>
\<summary\>19. UI State Pseudo-classes (\<code\>:enabled\</code\>, \<code\>:disabled\</code\>, \<code\>:checked\</code\>)\</summary\>
\<p\>These pseudo-classes target elements based on their current state in the user interface.\</p\>
\<ul\>
\<li\>\<code\>:enabled\</code\> / \<code\>:disabled\</code\>: Targets form elements that are available or unavailable for interaction.\</li\>
\<li\>\<code\>:checked\</code\>: Targets radio buttons or checkboxes that are selected.\</li\>
\</ul\>

```css
input[type=radio]:checked {
  border: 1px solid black;
}

input:disabled {
  background-color: #ccc;
}
```

\</details\>

\<details\>
\<summary\>20. Target Pseudo-class (\<code\>:target\</code\>)\</summary\>
\<p\>Used to style an element whose \<code\>id\</code\> attribute matches a URI fragment. For example, if the URL is \<code\>[http://example.com/index.html\#hello](http://example.com/index.html#hello)\</code\>, the \<code\>:target\</code\> pseudo-class will match the element with \<code\>id="hello"\</code\>.\</p\>

```html
<section id="hello">...</section>
```

```css
section:target {
  background-color: yellow;
}
```

\</details\>

\<details\>
\<summary\>21. Empty Pseudo-class (\<code\>:empty\</code\>)\</summary\>
\<p\>Selects elements that do not contain any children or text nodes. Whitespace, comments, and processing instructions are not considered children for this purpose.\</p\>

```css
div:empty {
  border: 1px solid red;
}
```

````html
<div>Hello</div>
<div></div>
<div></div><div> </div> <div><strong></strong></div> ```
</details>

<details>
<summary>22. Negation Pseudo-class (<code>:not()</code>)</summary>
<p>The <code>:not(x)</code> pseudo-class takes an argument (a selector) and selects elements that do <em>not</em> match that argument.</p>

```css
div:not(#container) {
  color: blue;
}
````

\<p\>This selects all \<code\>\&lt;div\&gt;\</code\> elements except for the one with the ID of \<code\>container\</code\>.\</p\>
\</details\>

-----

## Pseudo-element Selectors (`::`)

*Note: The double colon `::` syntax is used to distinguish pseudo-elements from pseudo-classes. Modern browsers support both `::` and the older single colon `:` syntax for backward compatibility with CSS2 pseudo-elements (`:before`, `:after`, etc.), but `::` is the current standard.*

\<details\>
\<summary\>23. Textual Pseudo-elements (\<code\>::first-line\</code\>, \<code\>::first-letter\</code\>)\</summary\>
\<ul\>
\<li\>\<code\>::first-line\</code\>: Targets the first line of a block-level element.\</li\>
\<li\>\<code\>::first-letter\</code\>: Targets the first letter of a block-level element.\</li\>
\</ul\>

```css
p::first-line {
  font-weight: bold;
  font-size: 1.2em;
}

p::first-letter {
  float: left;
  font-size: 2em;
  font-weight: bold;
  padding-right: 2px;
}
```

\</details\>

\<details\>
\<summary\>24. Generated Content Pseudo-elements (\<code\>::before\</code\>, \<code\>::after\</code\>)\</summary\>
\<p\>These create a new inline-level pseudo-element just inside the selected element, either before or after its content. They are used in conjunction with the \<code\>content\</code\> property.\</p\>

```css
p::after {
  content: " ∎"; /* Adds a square at the end of every paragraph */
  display: inline;
}
```

\</details\>

\<details\>
\<summary\>25. Fragment Pseudo-element (\<code\>::selection\</code\>)\</summary\>
\<p\>This pseudo-element applies styles to the part of a document that has been highlighted by the user (e.g., by clicking and dragging the mouse). Only a few properties can be used: \<code\>color\</code\>, \<code\>background\</code\>, \<code\>background-color\</code\>, and \<code\>text-shadow\</code\>.\</p\>
\<p\>For cross-browser compatibility, you should include vendor prefixes.\</p\>

```css
::-moz-selection {
  background: #ff7b29;
}
::selection {
  background: #ff7b29;
}
```

\</details\>

-----

## Structural & Positional Pseudo-classes

\<details\>
\<summary\>26. Nth Child Selectors (\<code\>:nth-child(n)\</code\>, \<code\>:nth-last-child(n)\</code\>)\</summary\>
\<p\>These selectors target elements based on their position among a group of siblings.\</p\>
\<ul\>
\<li\>\<code\>:nth-child(n)\</code\> counts from the beginning.\</li\>
\<li\>\<code\>:nth-last-child(n)\</code\> counts from the end.\</li\>
\</ul\>
\<p\>The argument \<code\>n\</code\> can be an integer, a keyword (\<code\>odd\</code\>, \<code\>even\</code\>), or a formula (\<code\>an+b\</code\>).\</p\>
\<p\>\<b\>Select the 3rd \<code\>\&lt;li\&gt;\</code\>:\</b\>\</p\>

```css
li:nth-child(3) {
  color: red;
}
```

\<p\>\<b\>Select every second item starting from the 3rd:\</b\>\</p\>

```css
li:nth-child(2n+3) { ... }
```

\<p\>\<b\>Select the first 4 items:\</b\>\</p\>

```css
li:nth-child(-n+4) { ... }
```

\</details\>

\<details\>
\<summary\>27. Nth of Type Selectors (\<code\>:nth-of-type(n)\</code\>, \<code\>:nth-last-of-type(n)\</code\>)\</summary\>
\<p\>This works similarly to \<code\>:nth-child\</code\>, but it only considers elements of the same type. This is useful when you have mixed element types within a parent.\</p\>
\<p\>\<b\>Select the 3rd \<code\>\&lt;p\&gt;\</code\> element inside its parent:\</b\>\</p\>

```css
p:nth-of-type(3) {
  color: red;
}
```

\<p\>\<b\>Select every odd paragraph, counting from the end:\</b\>\</p\>

```css
p:nth-last-of-type(2n+1) {
  border: 1px solid black;
}
```

\</details\>

\<details\>
\<summary\>28. First, Last, and Only Child Selectors\</summary\>
\<ul\>
\<li\>\<code\>:first-child\</code\>: Selects an element that is the first child of its parent.\</li\>
\<li\>\<code\>:last-child\</code\>: Selects an element that is the last child of its parent.\</li\>
\<li\>\<code\>:only-child\</code\>: Selects an element that is the only child of its parent.\</li\>
\</ul\>

```css
/* Remove top border from the very first list item */
ul li:first-child {
  border-top: none;
}

/* Target a paragraph only if it's the only element inside its parent div */
div p:only-child {
  color: red;
}
```

\</details\>

\<details\>
\<summary\>29. First, Last, and Only of Type Selectors\</summary\>
\<ul\>
\<li\>\<code\>:first-of-type\</code\>: Selects the first element of its type within its parent.\</li\>
\<li\>\<code\>:last-of-type\</code\>: Selects the last element of its type within its parent.\</li\>
\<li\>\<code\>:only-of-type\</code\>: Selects an element that is the only one of its type within its parent.\</li\>
\</ul\>

```css
/* Make the text bold if a list item is the only one of its kind (e.g., a ul with only one li) */
ul > li:only-of-type {
  font-weight: bold;
}
```

\</details\>

\<details\>
\<summary\>30. Combining Selectors: A Challenge\</summary\>
\<p\>Given the following HTML, how would you target only the second list item ("List Item 2")?\</p\>

```html
<div>
  <p> My paragraph here. </p>
  <ul>
    <li> List Item 1 </li>
    <li> List Item 2 </li>
  </ul>
  <ul>
    <li> List Item 3 </li>
    <li> List Item 4 </li>
  </ul>   
</div>
```

\<p\>\<b\>Solution 1:\</b\> Target the first \<code\>\&lt;ul\&gt;\</code\> of its type, then find its second \<code\>\&lt;li\&gt;\</code\> child.\</p\>

```css
ul:first-of-type &gt; li:nth-child(2) {
  font-weight: bold;
}
```

\<p\>\<b\>Solution 2:\</b\> Use the adjacent sibling selector to find the \<code\>\&lt;ul\&gt;\</code\> after the \<code\>\&lt;p\&gt;\</code\>, then find its last child.\</p\>

```css
p + ul li:last-child {
  font-weight: bold;
}
```

\<p\>\<b\>Solution 3:\</b\> Target the first \<code\>\&lt;ul\&gt;\</code\> of its type, then find the first \<code\>\&lt;li\&gt;\</code\> from the end (which is the second item).\</p\>

```css
ul:first-of-type li:nth-last-child(1) {
  font-weight: bold;
}
```

\</details\>
