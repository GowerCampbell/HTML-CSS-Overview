Positoning Content
To structure designs and help make content digestible

Positioning with floats property
Removing it from the normal flow of a page and then position it to the left or right of its parent element.
Flowing around the floated elements for <img> nest to <p> of text.

img {
  float: left;
}

Floats in Practice 

<header>
  <code>&#60;header&#62;</code>
</header>

<section>
  <code>&#60;section&#62;</code>
</section>

<aside>
  <code>&#60;aside&#62;</code>
</aside>

<footer>
  <code>&#60;footer&#62;</code>
</footer>

code {
  background: #2db34a;
  border-radius: 6px;
  color: #fff;
  display: block;
  font: 14px/24px "Source Code Pro", Inconsolata, "Lucida Console", Terminal, "Courier New", Courier;
  padding: 24px 15px;
  text-align: center;
}
header,
section,
aside,
footer {
  margin: 0 1.5% 24px 1.5%;
}
footer {
  margin-bottom: 0;
}


Here the <section> & <side> elements are block level elements that can be stacked.
section {
  float: left;
}
aside {
  float: right;
}
When an element is floated it will sit on the edge of its parent element or page.
Creating columns for reusable layout:
section {
  float: left;
  margin: 0 1.5%;
  width: 63%;
}
aside {
  float: right;
  margin: 0 1.5%;
  width: 30%;
}


Floats my chang an elements display value and relies on the vlue of block, should an inline element be floated
its display value will change/

header,
section,
aside,
footer {
  margin: 0 1.5% 24px 1.5%;
}
section {
  float: left;
  width: 63%;
}
aside {
  float: right;
  width: 30%;
}
footer {
  clear: both;
  margin-bottom: 0;
}

<header>
  <code>&#60;header&#62;</code>
</header>

<section>
  <code>&#60;section&#62; <br> float: left;</code>
</section>

<aside>
  <code>&#60;aside&#62; <br> float: right;</code>
</aside>

<footer>
  <code>&#60;footer&#62;</code>
</footer>

To position three <section> in  three-column row in stead of one column, we will need to adjust the width so they 
can sit next to each other.

code {
  background: #2db34a;
  border-radius: 6px;
  color: #fff;
  display: block;
  font: 14px/24px "Source Code Pro", Inconsolata, "Lucida Console", Terminal, "Courier New", Courier;
  padding: 24px 15px;
  text-align: center;
}
header,
section,
aside,
footer {
  margin: 0 1.5% 24px 1.5%;
}
section {
  float: left;
  width: 30%;
}
footer {
  clear: both;
  margin-bottom: 0;
}

Clearing & Containing floats 

The float property  is designed to allow content to warao around images.
Be warned that styles may not render if it is sat next to or is a parent elemnt.
Often effecting the margin and padding values aren't interpreted correctly.
Removing elements will cause them to wrap and use all available space around an floated element.

For instance layout without cleared or contained floats:

code {
  background: #2db34a;
  border-radius: 6px;
  color: #fff;
  display: block;
  font: 14px/24px "Source Code Pro", Inconsolata, "Lucida Console", Terminal, "Courier New", Courier;
  padding: 24px 15px;
  text-align: center;
}
header,
section,
aside,
footer {
  margin: 0 1.5% 24px 1.5%;
}
section {
  float: left;
}
aside {
  float: right;
}
section,
aside,
footer {
  margin-bottom: 0;
}

Clearing floats help us control the flow
div {
  clear: left;
}

footer {
  clear: both;
}

Preventing it from using all the space.

Another option is to containing floats, which helps is render elements that reside within a parent element.
Acting like a container, leaving the flow of the document normal outside of it.

.group:before,
.group:after {
  content: "";
  display: table;
}
.group:after {
  clear: both;
}
.group {
  clear: both;
  *zoom: 1;
}

Pseudo-elements; generated elements above and below the e;ement within the class of group.
And used as a table-level elements much like the block-level elements.
The elements in the class group clear any floats that may apeear above it/ 
<header>...</header>
<div class="group">
  <section>...</section>
  <aside>...</aside>
</div>
<footer>...</footer>

.group:before,
.group:after {
  content: "";
  display: table;
}
.group:after {
  clear: both;
}
.group {
  clear: both;
  *zoom: 1;
}
section {
  float: left;
  margin: 0 1.5%;
  width: 63%;
}
aside {
  float: right;
  margin: 0 1.5%;
  width: 30%;
}

This technique is known as a clearfix or cf. 
Used to representing and organising multiple sections or asides within the content.

Positioning with Inline-Block
Placing elements next to one another within a line.
And display elements using the height, width, padding, border and argin

section {
  display: inline-block;
  margin: 0 1.5%;
  width: 30%;
}
Howevero a  for elements not to be pushed to a new row, space between will need to be removed.

The solution is to put each new section on the same line as the previous closing tag
<header>...</header>
<section>
  ...
</section><section>
  ...
</section><section>
  ...
</section>
<footer>...</footer>
No longer does space between inline-block elements within HTML exist.
Another way is to to use an open HTML com-ment before the next inline blocks opening tag. 
<header>...</header>
<section>
  ...
</section><!--
--><section>
  ...
</section><!--
--><section>
  ...
 </section>
 <footer>...</footer>

Creating Reusable layouts (using either floats or inline-block elements to create a grid and then use floats
to wrap content. New css specfication flex and grid as they are now used.

<!DOCTYPE html>
<html lang="en">
  <head>
  <meta charset="utf-8">
  <title>Styles Conference</title>
  <link rel="stylesheet" href="./assets/stylesheets/main.css">
</head>
  <body>
  <header class="container group">
  <section class="container" >
    <h1 class="logo">
  <a href="index.html">Styles <br> Conference</a>
  </h1>
  </section>
  <h3>August 24&ndash;26th &mdash; Chicago, IL</h3>

  
   <nav>
    <a href="index.html" >Home</a>
    <a href="speakers.html">Speakers</a>
    <a href="schedule.html">Schedule</a>
    <a href="venue.html">Venue</a>
    <a href="register.html" >Register</a>
  </nav>

</header>
<section class="hero container">
  <h2>Dedicated to the Craft of Building Websites</h2>
  <p>Every year the brightest web designers and front-end developers descend on Chicago to discuss the latest technologies. Join us this August!</p>
   <a href="register.html" class="btn btn-alt">Register Now</a>
</section>

<section class="grid">
  <!-- Speakers -->
  <section class="col-1-3">
  <a href="speakers.html">
    <h5>Speakers</h5>
    <h3>World-Class Speakers</h3>
      </a>
<p>Joining us from all around the world are over twenty fantastic speakers, here to share their stories.</</p>
</section><!--Schedule--><section class="col-1-3">
  <a href="schedule.html">
    <h5>Schedule</h5>
    <h3>Three Inspiring Days</h3>
      </a>
<p>Enjoy three inspiring and action packed days of talks, gatherings and all-around goodtimes.</p>
</section><!--Venue--><section class="col-1-3">
  <a href="venue.html">
    <h5>Venue</h5>
    <h3>The Chicago Theatre</h3>
      </a>
<p>Within the heart of downtown Chicago, The Chicago Theatre will provide a beautiful conference venue.</p></section>
</section>

<footer class="primary-footer container group">
  <small>&copy; Styles Conference</small>
  <a href="index.html">Home</a>
    <a href="speakers.html">Speakers</a>
    <a href="schedule.html">Schedule</a>
    <a href="venue.html">Venue</a>
    <a href="register.html">Register</a>
  </nav>
</footer>
</body>
</html>

.container,
.grid {
  margin: 0 auto;
  width: 960px;
}
.container {
  padding-left: 30px;
  padding-right: 30px;
}

.grid,
.col-1-3,
.col-2-3 {
  padding-left: 15px;
  padding-right: 15px;
}

.col-1-3,
.col-2-3 {
  display: inline-block;
  vertical-align: top;
}

.col-1-3 {
  width: 33.33%;
}
.col-2-3 {
  width: 66.66%;
}

Uniqualy Positioning Elements
Using precise position: static; is default and is over written with a relative or absolute value.

Relative Positioning 
Allowing the elements to appear within the normal flow of a page , leaving spave for an element as intended while 
nit allowing other elements to flow around it but can givven offset properties
<div>...</div>
<div class="offset">...</div>
<div>...</div>
div {
  height: 100px;
  width: 100px;
}
.offset {
  left: 20px;
  position: relative;
  top: 20px;
}

Allowing it to sit between an overlap of the same element that moves by its own shape and aize.

Absolute Positioning
Confusing but the orginal spave and position of the element will not be preserved and are instead positioned 
in relation to a their relatively positioned parent element. By default if no relative element is found it 
will cascade to the body element.

<section>
  <div class="offset">...</div>
</section>

section {
  position: relative;
}
div {
  position: absolute;
  right: 20px;
  top: 20px;
}

Great for handling objects within a <div> container that allows it to sit in relation to a section element 

