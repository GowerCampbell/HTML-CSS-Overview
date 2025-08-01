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

id is used to identify a unique semantic elemnt or psuedo-class 

3. .error {
  color: red;
}

The class selector uses styling to apply to multiple groups of elements

4. 
a { color: red; }
ul { margin-left: 0; }

Type selector, using the element name to refer a chose.

## Combinator Selector

5. li a {
  text-decoration: none;
}

Known as an descendant selector that you use for a specific selector, and targets the children of those that are parents of a an element.

6. ul + p {
   color: red;
   }
Refer as an adjacent selector used by preseceding element.   
....</ul>

  <p> Lorem ipsum dolor sit amet, <a href="#" title="Some title">consectetur</a> adipisicing elit, sed do eiusmod tempor. </p>

Turns text red.

7. div#container > ul {
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

8. ul ~ p {
   color: red;
}
Sibling combinator that only targets <p> elements as long as they follow an <ul>

## Attribute Selectors

9. a[title] {
   color: green;
}
Selectiong only anchor tags that have a title attribute

10. a[href="https://webdesign.tutsplus.com"] {
  color: #83b348; /* Envato green */
}

This will style all anchor tags linked to that website while others are unaffected.

11. a[href*="tutsplus"] {
  color: #83b348; /* Envato green */
}

The star designates that the proceeding value must appear somewhere in the atriubute value setting a broad decalaration that affecting with the word tutsplus using specific reference.

12. a[href^="https"] {
   background: url(path/to/external/icon.png) no-repeat;
   padding-left: 10px;
}
Link:https://en.wikipedia.org/wiki/Help:External_link_icons
This lets a website display a little icon using a carat symbol to target all links use either href which begins with a https

13. a[href$=".jpg"] {
   color: red;
}
Allowing anchors, which link to an image end with .jpg

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

15.  a[data-info~="external"] {
   color: red;
}
a[data-info~="image"] {
   border: 1px solid black;
}
The (~) allows us to target an attribute which has a space-sepearated list of values.

This helps target extra values to make note of external links aswell as other links

<a href="path/to/image.jpg" data-info="external image"> Click Me, Fool </a>

/* Target data-info attr that contains the value "external" */
a[data-info~="external"] {
   color: red;
}
/* And which contain the value "image" */
a[data-info~="image"] {
  border: 1px solid black;
}

## Pseudo Selectors
A keyword added to a selector to let you style a specfic element. They create the first or the last child of an element.

16.
a:link { color: red; }
a:visited { color: purple; }

:link Targets all anchor tags which have yet to click on.
:visited Targets all that have been clicked on

17.
input[type=radio]:checked {
   border: 1px solid black;
}
Target a user interface element (radio button or checkbox)

18. The before and after pseudo classes to generate content around a selected element.

p::after {
    content: "some text string";
    display: block;
    }
For example, gradient shadows. Remember: pseudo element syntax :: for colon usage in pseudo classes use single :

19. div:hover {
  background: #e3e3e3;
}
 Styling as the user hovers over a element

a:hover {
 border-bottom: 1px solid black;
}

20. div:not(#container) {
   color: blue;
}
Selects all divs but not the one applied with the id of a container.

*:not(p) {
  color: green;
}

### ::pseudoElement
21. 

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

## Nth Child and Type Selectors

22. li:nth-child(3) {
   color: red;
}

Accepting an integer counts the <li> list item in the list element

23. li:nth-last-child(2) {
   color: red;}
Working from reverse this starts your integer count from the other direction.

24. ul:nth-of-type(3) {
     border: 1px solid black;}
    

Selecting according to the type of element, looking for the 5th element if unordered lists to create a border.

25. ul:nth-last-of-type(3) {
   border: 1px solid black;}

Working from reverse to target the desired element.

26. ul li:first-child {
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

28. div p:only-child {
   color: red;
}

Targets elements which are the only child of its parent

<div><p> My paragraph here. </p></div>
<div>
   <p> Two paragraphs total. </p>
   <p> Two paragraphs total. </p>
</div>
In this case,

Link: https://webdesign.tutsplus.com/the-30-css-selectors-you-must-memorize--net-16048t

