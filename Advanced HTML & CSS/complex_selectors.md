# Complex Selectors
How are they used to shape the cascade and determine the styles applied to elments on a page?

How to select different types of elements and in different states of use?

CSS3 has brought new selectors, opening a new world of opportunities and improvements to existing practices: base id, class and desendants selectors.

BASIC SELECTOR
---


1. * {
  margin: 0;
  padding: 0;
}
Targets all single element o the page, adding weight to the browser.

It can also be used with child selectors:
#container * {
 border: 1px solid black;
}
Target Every single element that is a child of the #container div

2. #container {
   width: 960px;
   margin: auto;
}

id is used to identify a unique semantic elemnt or psuedo-class on it s attribute value that can only be used once per page

3. .error {
  color: red;
}

The class selector uses styling to apply to multiple groups of elements based on its class atrribute value, reused on multiple elements

4. 
a { color: red; }
ul { margin-left: 0; }

Type selector, using the element name to refer how it is declared within HTML. 

## Combinator Selector
Link: https://css-tricks.com/child-and-sibling-selectors/
Also, known as child selectors that select eleents that fall within one another making them children of their parent element.

5. Descendant Selector 
li a {
  text-decoration: none;
}

Known as an descendant selector that you use for a specific selector, and targets the children of those that are parents of a an element. Does not come after directylu after the ancestor element setting up hierarchy for each element.

<h2>...</h2>
<article>
  <h2>This heading will be selected</h2>
  <div>
    <h2>This heading will be selected</h2>
  </div>
</article>

The article h2 selector is a descendant selector article h2 {...}

6. Adjacent Sibling Selector
Using tilde elements directly following after another sibling element using a, +, to identify an element following after its sibling. Looking at the adjacent sibling selecter: 

ul + p {
   color: red;
   }
Refer as an adjacent selector used by preseceding element selects element identified parent.
....</ul>

  <p> Lorem ipsum dolor sit amet, <a href="#" title="Some title">consectetur</a> adipisicing elit, sed do eiusmod tempor. </p>

Turns text red.

7. Direct Child Selector

Used by plaing a greater than sign, >, between the parent element and child within the selector. For example, article > p is a direct child only identufying within article element.

div#container > ul {
  border: 1px solid black;
}

<div id="container">
      <ul>
         <ul>
         <li> List Item
           <ul>
              <li> Child </li>
           </ul>
         </li>
         <li> List Item </li>
         <li> List Item </li>
         <li> List Item </li>
      </ul>
   </div>

Selecting only the direct children  with > to create a black border around
the Unordered list. This prents it from effecting the child of <li>

8. Sibling Selectors
Sharing a common parent, created using the tilde character, ~, between two elements within a sibling. Looking for p elements that follow h2 type and share the same parent. 

ul ~ p {
   color: red;
}
Sibling combinator that only targets <p> elements as long as they follow an <ul>

h2 ~ p {...}

  <p>...</p>
  <h2>...</h2>
  <p>This paragraph will be selected</p>
  
## Attribute Selectors
LInk: https://www.css3.info/preview/attribute-selectors/
Where an element selected is based on a class or ID value that is present and what value it contains.

9. Present selector
Identifys an element regardless of any value it selects based on if an attribute is present or not. Including the name [] to be qualified.

a[target] {
   color: green;
}

<a href="#" target="_blank">...</a>

Selectiong only anchor tags that have a title attribute

10. a[href="https://webdesign.tutsplus.com"] {
  color: #83b348; /* Envato green */
}

This will style all anchor tags linked to that website while others are unaffected.

11. Attribute Equals Selectors
A specific and exact matching to the same selector, for the, =, quaotations, "", and inside of the quotations to be desired matching attribute value.

a[href="http://google.com/"] {...}
<a href="http://google.com/">...</a>

11.5   Atribute Contains Selector 
Looks to find an element through all html that is based on part of an attribute value that is an exact match, using the * within the equals selectors.

a[href*="tutsplus"] {
  color: #83b348; /* Envato green */
}

The star designates that the proceeding value must appear somewhere in the atriubute value setting a broad decalaration that affecting with the word tutsplus using specific reference.

12. Attribute begins with Selector
Using a circumflex accent ^, within the square brackets of a selector between the attribute name and equals sign denotes that the attribute value


a[href^="https"] {
   background: url(path/to/external/icon.png) no-repeat;
   padding-left: 10px;
}
Link:https://en.wikipedia.org/wiki/Help:External_link_icons
This lets a website display a little icon using a carat symbol to target all links that use either href which begins with a https

13. Attribute Ends With Selector
Using the dollar sign to denote that attrubute needs to be at the end of a stated value.

a[href$=".jpg"] {
   color: red;
}
Allowing anchors, which link to an image end with .jpg to be colored RED

14. a[data-filetype="image"] {
   color: red;
}
a[href$=".jpg"],
a[href$=".jpeg"],
a[href$=".png"],
a[href$=".gif"],
a[href$=".webp"] {
   color: red;
}
Instead of creating multiple selectors 

Use <a href="path/to/image.jpg" data-filetype="image"> Image Link </a>

To target only those anchors
a[data-filetype="image"] {
   color: red;
}

15. Attribute Spaced Selector
When attributes are spaced apart only one word needs to be atched in order to make a selection.
   
a[data-info~="external"] {
   color: red;
}
a[data-info~="image"] {
   border: 1px solid black;
}
The (~) allows us to target an attribute which has a space-sepearated list of values.

This helps target extra values to make note of external links aswell as other links

<a href="path/to/image.jpg" data-info="external image"> Click Me, Fool </a>

15.5 Attribute Hyphenated Selector
Using the vertical line character, |, and it can target attributes that are hyphen separated with the stated value.
CSS
a[lang|="en"] {...}
HTML
<a href="#" lang="en-US">...</a>


## Pseudo-classes Selectors
A keyword added to a selector to let you style a specfic element. They create the first or the last child of an element. 

16. Link Pseudo-Classes

a:link { color: red; }
a:visited { color: purple; }

:link Targets all anchor tags which have yet to click on.
:visited Targets all that have been clicked on

17.
input[type=radio]:checked {
   border: 1px solid black;
}
Target a user interface element (radio button or checkbox)

19. User Action Pseudo-classes
Including a :hover, :active and :focus based on user actions

a:hover {...}
/* Picks up the mouse cursor */

a:active {...}
/* When A User Engages an element */

a:focus {...}
/* Applied to the focus point of the page.

For instance
div:hover {
  background: #e3e3e3;
}
 Styling as the user hovers over a element

a:hover {
 border-bottom: 1px solid black;
}

19.3 User Interface State Pseudo-Classes
Interface state of elements
For example :enabled, :disabled, :checked and :indeterminate

The selects an input that is in the default state of enabled and available while the :disabled selects an input that is not available.
input:enabled {...}
input:disabled {...}

The :checked works on checkboxes or radio buttons.
When something is neither selected or unselected it lives in an indeterminate state.
input:checked {...}
input:indeterminate {...}

19.6 Target Pseudo Class
Used to style elements ID attribute that mataches a URI fragment, using 
it to find an identifier within the URI using the # that creates an ID
for example: The URL http://example.com/index.html#hello from the section:
HTML
<section id="hello">...</section>

CSS
section:target {...}

19.9 Empty Pseudo-classes
Do not contain children or text nodes to be selected. 
Instead it uses comments, processing instructions and empty text nodes considered children, that are not teated. This will look for elements that contain a comment and must be a child of the <div>
div:empty {...}

<div>Hello</div>
<div><!-- Coming soon --></div><!-- This div will be selected -->
<div></div><!-- This div will be selected -->
<div> </div>
<div><strong></strong></div>

20. Negation Pseudo Class
:not(x) sets an argument that filters my selection:

div:not(#container) {
   color: blue;
}
Selects all divs but not the one applied with the id of a container.

*:not(p) {
  color: green;
}

An element not represented by argument.

### ::PseudoElement
Dynamic elements that dont exist and when used it within pseudo elemenets that allow unique parts of the page to be styliesed and ocan be only used within one selector at a given time.

21. Textual Pseudo-elements
In demonstration:

p::first-line {
   font-weight: bold;
   font-size: 1.2em;
}
Targets the first line of a paragraph 
Applied only to block-level elements to take effect.

Or

p::first-letter {
   float: left;
   font-size: 2em;
   font-weight: bold;
   font-family: cursive;
   padding-right: 2px;}

the first letter of that element consider compatibility namly
(:first-line, frirst-letter, :before and :after) they are both valid but only not supported by IE8 that can be read by screen readers

18. Generated Content Pseudo-Elements
Creating new inline element inside the selected element, used in conjunction with the content propert to add information to a page.

The before and after pseudo elements to generate content around a selected element.

p::after {
    content: "some text string";
    display: block;
    }
For example, gradient shadows. Remember: pseudo element syntax :: for colon usage in pseudo classes use single :

## Fragment Pseudo-element
The ::selection highlights the user actions that is used within the part of the document. The selection may then be stylized, however only by useing color, background, background-color and text-shadow properties. 

Single Colon (:) versus Double Colons (::)
This is used to differentiate pseudo classses from pseudo-elements, though browser supports multiple elements. 

When selecting any of the text within the browser ::-moz-selection to ensure that the elements are supported.

::-moz-selection {
    background: #ff7b29;
}
::selection {
  background: #ff7b29;
}


## Nth Child and Type Selectors
### Structural & Position Pseudo-classes
Based off where elements reside in the document tree, these structural, position based pseudo classes

22. :nth-child(n) & nth-last-child(n)
Works on the document model tree to search values from elements children.

li:nth-child(3) {
   color: red;
}

<ul>
  <li>...</li>
  <li>...</li>
  <li>This list item will be selected</li>

Accepting an integer counts the <li> list item in the list element yielding the result. Consider changes: li:nth-child(2n+3) {...}

<ul>
  <li>...</li>
  <li>...</li>
  <li>This list item will be selected</li>
  <li>...</li>
  <li>This list item will be selected</li>

Changing the expression again. We can identify the top 4 items to be selected

li:nth-child(-n+4) {...}

<ul>
  <li>This list item will be selected</li>
  <li>This list item will be selected</li>
  <li>This list item will be selected</li>
  <li>This list item will be selected</li>

By adding a negatve interger before the n argument 
li:nth-child(-2n+5) identifies every second item because of recurring numbers

<ul>
  <li>This list item will be selected</li>
  <li>...</li>
  <li>This list item will be selected</li>
  <li>...</li>
  <li>This list item will be selected</li>
  <li>...</li>

23. li:nth-last-child(2) {
   color: red;}
Working from reverse this starts your integer count from the other direction. Switching the direction of counting from the end of the document this identifys every list item.

li:nth-last-child(3n+2) {...}

<ul>
  <li>...</li>
  <li>This list item will be selected</li>
  <li>...</li>
  <li>...</li>
  <li>This list item will be selected</li>
  <li>...</li>

25. :nth-of-type(n) 
Counting elements of their type allowing it to skip divisions, misc elements etc..

ul:nth-of-type(3n) {
     border: 1px solid black;}
    
Selecting according to the type of element, looking for the 3th element if unordered lists to create a border.

<article>
  <h1>...</h1>
  <p>...</p>
  <p>...</p>
  <p>This paragraph will be selected</p>

25. p:nth-last-of-type(2n+1) {
   border: 1px solid black;}|

Selecting every second paragraph from the end of a paragraph.
 <p>This paragraph will be selected</p>
  <p>...</p>
  <h2>...</h2>
<p>This paragraph will be selected</p>
  <p>...</p>
  <p>This paragraph will be selected</p>
</article>

Working from reverse to target the desired element.

26. Structure & Position of Classes

li:first-child {...}
li:last-child {...}
div:only-child {...}

ul li:first-child {
   border-top: none;
}

Targeting the first child of an elements parents. 

27. ul > li:last-child {
   color: green;
}

Targeting only the last child of an descended element.

ul {
 width: 200px;
 background: #292929;
 color: white;
 list-style: none;
 padding-left: 0;
}
li {
 padding: 10px;
 border-bottom: 1px solid black;
 border-top: 1px solid #3c3c3c;
}

Helping to add depth to your list use a border-bottom with differing coloring to create different shades to a list item from its background.

28. 

div p:only-child {
   color: red;
}

Targets elements which are the only child of its parent

<div><p> My paragraph here. </p></div>
<div>
   <p> Two paragraphs total. </p>
   <p> Two paragraphs total. </p>
</div>
In this case, the div will only target the first <p></p>

29. li:only-of-type {
    font-weight: bold;}

This targets elements that do not have any siblings within its parent container, as all <ul>  which have only single list item to accomplish a task.

ul > li:only-of-type {
   font-weight: bold;
}

30. The first-of-type pseudo class allows you to select the first siblings of its type.

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

How would you target the second list item?

Soloution 1
ul:first-of-type > li:nth-child(2) {
     font-weight: bold;
}

Solution 2

p + ul li:last-child {
    font-weight: bold;
    }

Solution 3
ul:first-of-type li:nth-last-child(1) {
     font-weight: bold;
}
    

Link: https://webdesign.tutsplus.com/the-30-css-selectors-you-must-memorize--net-16048t

