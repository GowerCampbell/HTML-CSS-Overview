

# Complex Selectors

\<details\>
\<summary\>How do complex selectors shape the cascade and determine which styles apply to an element?\</summary\>
\<p\>Complex selectors play a crucial role in CSS by increasing the \<b\>specificity\</b\> of a rule. The browser's cascade algorithm uses specificity to decide which style rule applies if multiple rules target the same element. A more specific selector (like an ID selector \<code\>\#main\</code\>) will override a less specific one (like a type selector \<code\>div\</code\>). By combining selectors (e.g., \<code\>\#main \> article .highlight\</code\>), you create highly specific rules that precisely target elements, giving you fine-grained control over the final appearance of your webpage.\</p\>
\</details\>

\<details\>
\<summary\>How can you select different types of elements and target them in various states?\</summary\>
\<p\>CSS provides a wide array of selectors for this purpose. You can select elements by their \<b\>type\</b\> (\<code\>p\</code\>, \<code\>h1\</code\>), \<b\>ID\</b\> (\<code\>\#unique\</code\>), or \<b\>class\</b\> (\<code\>.common\</code\>). You can also select them based on their relationship to other elements (descendants, children, siblings) or their attributes (\<code\>[type="text"]\</code\>). To target elements in different states, you use \<b\>pseudo-classes\</b\>, which let you style elements based on user actions (\<code\>:hover\</code\>, \<code\>:focus\</code\>), their state in the UI (\<code\>:checked\</code\>, \<code\>:disabled\</code\>), or their position in the document tree (\<code\>:first-child\</code\>, \<code\>:nth-of-type(2)\</code\>).\</p\>
\</details\>

CSS3 has brought new selectors, opening a new world of opportunities and improvements to the base ID, class, and descendant selectors.

-----

## Basic Selectors

Basic selectors target elements based on their type, class, or ID.

\<details\>
\<summary\>\<code\>*\</code\> (Universal Selector)\</summary\>
\<p\>Targets every single element on the page. Using it can add weight to the browser's rendering process.\</p\>
\<pre\>\<code\>* {
margin: 0;
padding: 0;
}\</code\>\</pre\>
\<p\>It can also be combined with other selectors to target all descendants of an element:\</p\>
\<pre\>\<code\>\#container \* {
border: 1px solid black;
}\</code\>\</pre\>
\</details\>

\<details\>
\<summary\>\<code\>\#id\</code\> (ID Selector)\</summary\>
\<p\>The ID selector targets a unique element based on the value of its \<code\>id\</code\> attribute. An ID should only be used once per page.\</p\>
\<pre\>\<code\>\#container {
width: 960px;
margin: auto;
}\</code\>\</pre\>
\</details\>

\<details\>
\<summary\>\<code\>.class\</code\> (Class Selector)\</summary\>
\<p\>The class selector styles a group of elements based on the value of their \<code\>class\</code\> attribute. A class can be reused on multiple elements.\</p\>
\<pre\>\<code\>.error {
color: red;
}\</code\>\</pre\>
\</details\>

\<details\>
\<summary\>\<code\>element\</code\> (Type Selector)\</summary\>
\<p\>The type selector targets all elements of a given type, referring to the element's name as declared in the HTML.\</p\>
\<pre\>\<code\>a { color: red; }
ul { margin-left: 0; }\</code\>\</pre\>
\</details\>

-----

## Combinator Selectors

Combinators define the relationship between two or more selectors, allowing you to target elements based on their position in the document tree.

\<details\>
\<summary\>\<code\>A B\</code\> (Descendant Selector)\</summary\>
\<p\>This selector targets all elements 'B' that are descendants (children, grandchildren, etc.) of element 'A', regardless of how deeply they are nested.\</p\>
\<pre\>\<code\>li a {
text-decoration: none;
}\</code\>\</pre\>
\</details\>

\<details\>
\<summary\>\<code\>A \> B\</code\> (Direct Child Selector)\</summary\>
\<p\>This selector targets all elements 'B' that are direct children of element 'A'. It uses a greater-than sign (\<code\>\>\</code\>) between the parent and child.\</p\>
\<pre\>\<code\>div\#container \> ul {
border: 1px solid black;
}\</code\>\</pre\>
\<p\>In the example below, only the first \<code\>\<ul\>\</code\> (the direct child of \<code\>\#container\</code\>) gets a border. The nested \<code\>\<ul\>\</code\> inside the \<code\>\<li\>\</code\> is not affected.\</p\>
\<pre\>\<code\>\&lt;div id="container"\&gt;
\&lt;ul\&gt; \&lt;\!-- This ul is selected --\&gt;
\&lt;li\&gt; List Item
\&lt;ul\&gt; \&lt;\!-- This ul is NOT selected --\&gt;
\&lt;li\&gt; Child \&lt;/li\&gt;
\&lt;/ul\&gt;
\&lt;/li\&gt;
\&lt;/ul\&gt;
\&lt;/div\&gt;\</code\>\</pre\>
\</details\>

\<details\>
\<summary\>\<code\>A + B\</code\> (Adjacent Sibling Selector)\</summary\>
\<p\>This selector targets the element 'B' that immediately follows element 'A', provided they share the same parent. It uses a plus sign (\<code\>+\</code\>).\</p\>
\<pre\>\<code\>ul + p {
color: red;
}\</code\>\</pre\>
\<p\>This will turn the text of the first paragraph directly following a \<code\>ul\</code\> red.\</p\>
\</details\>

\<details\>
\<summary\>\<code\>A \~ B\</code\> (General Sibling Selector)\</summary\>
\<p\>This selector targets all elements 'B' that follow element 'A', as long as they share the same parent. It is less strict than the adjacent sibling selector and uses a tilde (\<code\>\~\</code\>).\</p\>
\<pre\>\<code\>h2 \~ p {
color: red;
}\</code\>\</pre\>
\<p\>This targets any \<code\>\&lt;p\&gt;\</code\> element that comes after an \<code\>\&lt;h2\&gt;\</code\> and shares the same parent.\</p\>
\</details\>

-----

## Attribute Selectors

These selectors target elements based on the presence or value of their attributes.

\<details\>
\<summary\>\<code\>[attribute]\</code\> (Presence Selector)\</summary\>
\<p\>Selects an element if the specified attribute is present, regardless of its value.\</p\>
\<pre\>\<code\>a[target] {
color: green;
}\</code\>\</pre\>
\<p\>This selects any anchor tag that has a \<code\>target\</code\> attribute.\</p\>
\</details\>

\<details\>
\<summary\>\<code\>[attribute="value"]\</code\> (Equals Selector)\</summary\>
\<p\>Selects an element if the attribute has an exact matching value.\</p\>
\<pre\>\<code\>a[href="[https://webdesign.tutsplus.com](https://webdesign.tutsplus.com)"] {
color: \#83b348;
}\</code\>\</pre\>
\</details\>

\<details\>
\<summary\>\<code\>[attribute\*="value"]\</code\> (Contains Selector)\</summary\>
\<p\>Selects an element if the attribute value contains the specified substring. The asterisk (\<code\>*\</code\>) designates that the value must appear somewhere in the attribute.\</p\>
\<pre\>\<code\>a[href*="tutsplus"] {
color: \#83b348;
}\</code\>\</pre\>
\</details\>

\<details\>
\<summary\>\<code\>[attribute^="value"]\</code\> (Begins With Selector)\</summary\>
\<p\>Selects an element if its attribute value begins with the specified string. It uses a circumflex accent (\<code\>^\</code\>).\</p\>
\<pre\>\<code\>a[href^="https"] {
background: url(path/to/external/icon.png) no-repeat;
padding-left: 10px;
}\</code\>\</pre\>
\</details\>

\<details\>
\<summary\>\<code\>[attribute$="value"]\</code\> (Ends With Selector)\</summary\>
\<p\>Selects an element if its attribute value ends with the specified string. It uses a dollar sign (\<code\>$\</code\>).\</p\>
\<pre\>\<code\>a[href$=".jpg"] {
color: red;
}\</code\>\</pre\>
\</details\>

\<details\>
\<summary\>\<code\>[attribute\~="value"]\</code\> (Spaced Selector)\</summary\>
\<p\>Selects an element if the attribute has a space-separated list of values, and one of those values is an exact match. It uses a tilde (\<code\>\~\</code\>).\</p\>
\<pre\>\<code\>a[data-info\~="external"] {
color: red;
}
a[data-info\~="image"] {
border: 1px solid black;
}\</code\>\</pre\>
\<p\>HTML Example:\</p\>
\<pre\>\<code\>\&lt;a href="path/to/image.jpg" data-info="external image"\&gt; Click Me \&lt;/a\&gt;\</code\>\</pre\>
\</details\>

\<details\>
\<summary\>\<code\>[attribute|="value"]\</code\> (Hyphenated Selector)\</summary\>
\<p\>Selects an element if the attribute value is exactly "value" or starts with "value" immediately followed by a hyphen (\<code\>-\</code\>). It uses a vertical line (\<code\>|\</code\>). This is often used for language codes.\</p\>
\<pre\>\<code\>a[lang|="en"] {
/\* Styles links with lang="en" or lang="en-US", etc. \*/
}\</code\>\</pre\>
\</details\>

-----

## Pseudo-Selectors

### Pseudo-classes (State & Structure)

A pseudo-class is a keyword added to a selector that specifies a special state of the selected element(s). They are denoted by a single colon (`:`).

\<details\>
\<summary\>\<code\>:link\</code\> & \<code\>:visited\</code\>\</summary\>
\<p\>These pseudo-classes style anchor tags based on the user's Browse history.\</p\>
\<ul\>
\<li\>\<code\>:link\</code\>: Targets anchor tags that have not yet been clicked.\</li\>
\<li\>\<code\>:visited\</code\>: Targets anchor tags that have already been clicked.\</li\>
\</ul\>
\<pre\>\<code\>a:link { color: red; }
a:visited { color: purple; }\</code\>\</pre\>
\</details\>

\<details\>
\<summary\>\<code\>:hover\</code\>, \<code\>:active\</code\>, & \<code\>:focus\</code\>\</summary\>
\<p\>These user-action pseudo-classes apply styles based on user interaction.\</p\>
\<ul\>
\<li\>\<code\>:hover\</code\>: Applied when the user's mouse cursor is over an element.\</li\>
\<li\>\<code\>:active\</code\>: Applied when a user clicks on or otherwise engages an element.\</li\>
\<li\>\<code\>:focus\</code\>: Applied to the element that currently has focus (e.g., a form input).\</li\>
\</ul\>
\<pre\>\<code\>a:hover {
border-bottom: 1px solid black;
}\</code\>\</pre\>
\</details\>

\<details\>
\<summary\>\<code\>:checked\</code\>, \<code\>:disabled\</code\>, \<code\>:enabled\</code\>, \<code\>:indeterminate\</code\>\</summary\>
\<p\>These UI state pseudo-classes target form elements based on their current state.\</p\>
\<ul\>
\<li\>\<code\>:checked\</code\>: Applies to radio buttons or checkboxes that are selected.\</li\>
\<li\>\<code\>:disabled\</code\>: Applies to an input that is not available for interaction.\</li\>
\<li\>\<code\>:enabled\</code\>: Applies to an input that is available for interaction (the default state).\</li\>
\<li\>\<code\>:indeterminate\</code\>: Applies to an element (like a checkbox) that is in a state of being neither checked nor unchecked.\</li\>
\</ul\>
\<pre\>\<code\>input[type=radio]:checked {
border: 1px solid black;
}
input:disabled {
background-color: \#eee;
}\</code\>\</pre\>
\</details\>

\<details\>
\<summary\>\<code\>:target\</code\>\</summary\>
\<p\>This pseudo-class styles an element whose ID attribute matches the fragment identifier of the page's URI. For example, the URL \<code\>[http://example.com/index.html\#hello](http://example.com/index.html#hello)\</code\> would target the element with \<code\>id="hello"\</code\>.\</p\>
\<pre\>\<code\>section:target {
background-color: yellow;
}\</code\>\</pre\>
\</details\>

\<details\>
\<summary\>\<code\>:not(x)\</code\> (Negation Pseudo-class)\</summary\>
\<p\>This pseudo-class takes another selector as an argument and targets elements that are *not* represented by that argument.\</p\>
\<pre\>\<code\>div:not(\#container) {
color: blue;
}\</code\>\</pre\>
\<p\>This selects all \<code\>\&lt;div\&gt;\</code\> elements except for the one with the ID of `container`.\</p\>
\</details\>

\<details\>
\<summary\>\<code\>:empty\</code\>\</summary\>
\<p\>This pseudo-class selects elements that have no children, including text nodes. Whitespace is considered a child, so an element with a space inside it is not empty. Comments and processing instructions are also not considered children.\</p\>
\<pre\>\<code\>div:empty {
border: 1px dashed red;
}\</code\>\</pre\>
\<p\>The following elements would be selected:\</p\>
\<pre\>\<code\>\&lt;div\&gt;\&lt;\!-- Coming soon --\&gt;\&lt;/div\&gt; \&lt;\!-- This div will be selected --\&gt;
\&lt;div\&gt;\&lt;/div\&gt; \&lt;\!-- This div will be selected --\&gt;\</code\>\</pre\>
\</details\>

### Pseudo-elements (Generated & Virtual)

A pseudo-element is a keyword added to a selector that lets you style a specific part of the selected element(s). They are denoted by a double colon (`::`) in modern CSS to distinguish them from pseudo-classes.

\<details\>
\<summary\>\<code\>::before\</code\> & \<code\>::after\</code\>\</summary\>
\<p\>These pseudo-elements create a new inline element just before or just after the content of the selected element. They are used in conjunction with the \<code\>content\</code\> property to add generated information to a page.\</p\>
\<pre\>\<code\>p::after {
content: " 🔚";
display: inline;
}\</code\>\</pre\>
\</details\>

\<details\>
\<summary\>\<code\>::first-line\</code\> & \<code\>::first-letter\</code\>\</summary\>
\<p\>These textual pseudo-elements target a specific part of an element's text content. They can only be applied to block-level elements.\</p\>
\<ul\>
\<li\>\<code\>::first-line\</code\>: Targets the first line of text within an element.\</li\>
\<li\>\<code\>::first-letter\</code\>: Targets the first letter of text within an element.\</li\>
\</ul\>
\<pre\>\<code\>p::first-letter {
float: left;
font-size: 2em;
font-weight: bold;
padding-right: 2px;
}\</code\>\</pre\>
\</details\>

\<details\>
\<summary\>\<code\>::selection\</code\>\</summary\>
\<p\>This pseudo-element styles the portion of a document that has been highlighted by the user (e.g., by clicking and dragging the mouse). Styling is limited to `color`, `background`, `background-color`, and `text-shadow` properties.\</p\>
\<pre\>\<code\>/\* For Firefox */
::-moz-selection {
background: \#ff7b29;
}
/* For other browsers \*/
::selection {
background: \#ff7b29;
}\</code\>\</pre\>
\</details\>

-----

## Nth-Child & Type Selectors

These pseudo-classes select elements based on their position (or their type and position) among a group of siblings.

\<details\>
\<summary\>\<code\>:nth-child(n)\</code\> & \<code\>:nth-last-child(n)\</code\>\</summary\>
\<p\>These pseudo-classes select elements based on their position among their siblings.\</p\>
\<ul\>
\<li\>\<code\>:nth-child(n)\</code\>: Counts from the beginning.\</li\>
\<li\>\<code\>:nth-last-child(n)\</code\>: Counts from the end.\</li\>
\</ul\>
\<p\>The argument `n` can be a number, a keyword (`odd`, `even`), or a formula (`an+b`).\</p\>
\<pre\>\<code\>/\* Selects the third list item \*/
li:nth-child(3) {
color: red;
}

/\* Selects all even list items \*/
li:nth-child(even) {
background-color: \#f2f2f2;
}

/\* Selects every third list item, starting with the second \*/
li:nth-child(3n+2) {
font-weight: bold;
}\</code\>\</pre\>

\</details\>

\<details\>
\<summary\>\<code\>:nth-of-type(n)\</code\> & \<code\>:nth-last-of-type(n)\</code\>\</summary\>
\<p\>These work similarly to `nth-child`, but they only count elements of the same type. This is useful when siblings are of different types (e.g., `p`, `h2`, `p`).\</p\>
\<pre\>\<code\>/\* Selects the third paragraph inside its parent, ignoring other element types \*/
p:nth-of-type(3) {
color: blue;
}

/\* Selects every odd paragraph from the end of its parent \*/
p:nth-last-of-type(2n+1) {
border: 1px solid black;
}\</code\>\</pre\>

\</details\>

\<details\>
\<summary\>\<code\>:first-child\</code\>, \<code\>:last-child\</code\>, & \<code\>:only-child\</code\>\</summary\>
\<p\>These are shortcuts for common `nth-child` selections.\</p\>
\<ul\>
\<li\>\<code\>:first-child\</code\>: Selects an element that is the first child of its parent. Same as \<code\>:nth-child(1)\</code\>.\</li\>
\<li\>\<code\>:last-child\</code\>: Selects an element that is the last child of its parent. Same as \<code\>:nth-last-child(1)\</code\>.\</li\>
\<li\>\<code\>:only-child\</code\>: Selects an element that is the only child of its parent.\</li\>
\</ul\>
\<pre\>\<code\>/\* Targets a paragraph that is the only element inside its parent div \*/
div p:only-child {
color: red;
}\</code\>\</pre\>
\</details\>

\<details\>
\<summary\>\<code\>:first-of-type\</code\>, \<code\>:last-of-type\</code\>, & \<code\>:only-of-type\</code\>\</summary\>
\<p\>These are shortcuts for common `nth-of-type` selections.\</p\>
\<ul\>
\<li\>\<code\>:first-of-type\</code\>: Selects the first element of its type among its siblings.\</li\>
\<li\>\<code\>:last-of-type\</code\>: Selects the last element of its type among its siblings.\</li\>
\<li\>\<code\>:only-of-type\</code\>: Selects an element that has no other siblings of the same type.\</li\>
\</ul\>
\<pre\>\<code\>/\* Targets a list item if it's the only one in the list \*/
ul \> li:only-of-type {
font-weight: bold;
}\</code\>\</pre\>
\</details\>

\<details\>
\<summary\>Selector Challenge: Target the second list item\</summary\>
\<p\>Given the following HTML, how would you target only "List Item 2"?\</p\>
\<pre\>\<code\>\&lt;div\&gt;
\&lt;p\&gt; My paragraph here. \&lt;/p\&gt;
\&lt;ul\&gt;
\&lt;li\&gt; List Item 1 \&lt;/li\&gt;
\&lt;li\&gt; List Item 2 \&lt;/li\&gt;
\&lt;/ul\&gt;
\&lt;ul\&gt;
\&lt;li\&gt; List Item 3 \&lt;/li\&gt;
\&lt;li\&gt; List Item 4 \&lt;/li\&gt;
\&lt;/ul\&gt;
\&lt;/div\&gt;\</code\>\</pre\>
\<p\>\<b\>Solution 1:\</b\>\</p\>
\<pre\>\<code\>ul:first-of-type \> li:nth-child(2) {
font-weight: bold;
}\</code\>\</pre\>
\<p\>\<b\>Solution 2:\</b\>\</p\>
\<pre\>\<code\>p + ul li:last-child {
font-weight: bold;
}\</code\>\</pre\>
\<p\>\<b\>Solution 3:\</b\>\</p\>
\<pre\>\<code\>ul:first-of-type li:nth-last-child(1) {
font-weight: bold;
}\</code\>\</pre\>
\</details\>
