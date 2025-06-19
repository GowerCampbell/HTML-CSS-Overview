# Recommended By #100Dev this includes my knotes from my reading of class-3 homework tht will be converted to ankiweb-cards. Link: https://learnlayout.com/

----

## Table of Contents
- no layout
- the "disply" property
- margin: auto;
- max-width
- the box model
- box-sizing
- position
- position example
- float
- clear
- the clearfix hack
- float layout example
- percent width
- media queries
- inline-block
- inline-block layout
- column
- flexbox
- css frameworks
- about this site

---

no layout is better if you just want one big column of content.
However is if you use the 'display' property to stylise:
What inline, block(On another line), inline-block(inline but treated as a block) and inherit from a container. There is also, flex, which (reserch this)

---

The "display" property

How is the display the controlling element? Wht does every elemnt have a default display vlue depending on what type of element it is? Which default can block or inline be an element?

block.
why is div a block-level? Other common ones are 'p' and 'form' and in html5 header, footer, section and more. 

inline.
span is the standard inline element. An inline element can wrap some text inside a paragraph <span> like this </span> without disrupting the flow of thta paragraph. Also, <a> is the most common and is used for links.

none
Specialized elements such as scripts, arent shown to run specilised jvascript programs?

other display elements?
Heres things like a list-item or flex which we look at later?

Extra credit
Making an inline <li> elements for horizontl menus.

---

margin: auto;

#main {
width: 600px;
margin 0 auo;
}

<div id="main">
Wby does setting the width of a block-level element will prevent it from stretching out to the edges of its container to the left and right?  When you set the left and right margins to auto to horizontally center that element within its container, why does the remaining space split evently between the margins.

When a browser window is narrower than the width of my element will the browser resolves this by creating a horizontal scrollbar on the page. </div>


---

max-width

#main {
max-width: 600px;
margin: 0 auto;
}

<div id="main">
Why is using the max-width instead of width improve a browsers handling of small browsers? 
Does it stop a box from resizing?
</div>

---

the box model

When you set the width of an element, does the element appear bigger than what you set? REmember that a elements border and padding will stretch out the element when specified with a width>

.simple {
width: 500px;
margin: 20px auto;
}

.fancy {
width: 500px;
margin: 20px auto;
padding: 50px;
border-width: 10px;
}

<div class="simple'>
I'm smaller"
  </div>

<div class="fancy">
And I'm bigger!
</div>

Padding provides the box with more content to contain.

---

box-sizing

Is often unintuitive, so the css property box-sizing was created so what does it do?

.simple {
width: 500px;
margin: 20px auto;
-webkit-box-sizing: border-box;
-moz-box-sizing: border-box;
box-sizing: border-box;
}

.fancy {
width: 500px;
margin: 20px auto;
padding: 50px;
border: solid blue 10px;
-webkit-box-sizing: border-box;
-moz-box-sizing: border-box;
box-sizing: border-box;
}

<div class ="simple">
  The width is now the same size?
</div>

<div class="fancy"
Hooray!
  </div>
Ensuring all elements are sized in an intuitive way without being effected by the browers prefixes.

---

position

.static {
position: static;
}

<div class="static">
  When we want an element to not be positioed in any special way, we use the static element, which is said to not be position? What can we use with it when we set it to anything else said to be positioned?
</div>

.relative1 {
position: relative;
}

.relative2 {
position: relative;
top: -20px;
left: 20px;
background-color: white;
width: 500px
}

<div class="relative1">
  relative behaves the same as static unless you add extra properties
</div>

<div class="relative2">
  Why is it important to set the top, right, bottom, and left properties of a relatively positioned element? How will it be adjusted from its normal position. Other content will not be adjusted to fit into the gap left by the element.
}

fixed
How can a fixed element be positioned relative to a viewport so that it stays in the same place even if the page is scrolled?

.fixed {
position: fixed;
bottom: 0;
right: 0;
width: 200px;
background-color: white;
}

How do we ensure a fixed element does not leave a gap in the page? And that it travels with you as view the contents of this page?

absolute

When we use ansolute? How does it position itself from the nearest ancestor? Will this be the viewport or will that be a relative element in the viewport? If it uses the document body, how will it move along the page when its scrolling. Rememeber a positioned element is one whose position is not?

.relative {
position: relative;
width: 600px;
height: 400px;
}

.absolute {
position: absolute;
top: 120px;
right: 0;
width: 300px;
height: 200px;
}

<div class="relative">
How is a relatively-positioned element not static? If this was position: static; how would it escape when it is positioned relative to a documents body </div>

<div class="absolute">
When am element is absolutely-positioned, will it be relative to its parent?

position example

.container {
position: relative;
}

nav {
position: absolute;
left: 0px
width: 200px;
}

section {
/* position is static by default */
margin-left: 200px;

footer {
position: fixed;
bottom: 0;
left: 0;
height: 70px;
background-color: white;
width: 100%;
}

body {
margin-bottom: 120px;
}

<div class="container">

<nav> 
Home 
Taco Menu 
DraftList
Hours
Directions
Contact
</nav>

<section>
Is it important for the margin-left style be used by the sections to make sure there is room for the nav? How do you prevent the absolute and static elements from overlapping? </section>

Why does this example work when container is taller than the nav? How do we ensure the nav would overflow outside of its container? </section>

</div>

<footer>
When using a fixed header? Do you need to a fixed margin at the bottom of your htmls body
</footer>

---

float

Why is float intended for wrapping text around the image?
img {
float: right;
margin: 0 0 1em 1em;
}

---
clear


  
