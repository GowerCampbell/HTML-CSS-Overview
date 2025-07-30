# Detailed Positioning
Techniques to create a layout and positioning content on a page, for instance the abbility to flaot elements, using a clean layout. Consider the use of relative or absolute positioning. Learning how to contain floats, using the x, y axis as well as the z axis.

## Containing Floats.
In the natural flow of the website using a layout that allows elements to interact based on size and the size of a containing parent. 

How floated elements become dependent on other elements positioned around it?

Depends on the DOM (Document Object Model) and what surrounds an element.

What is the DOM
*API (Application Programming Interface:  a set of rules and protocols that allows different software applications to communicate with each other and exchange data, features, and functionality.) 

The DOM is an API for HTML & XML(markup languages to structure elements) that represent all the different elements and their relationship between the parent and child/siblings.

A Float is a CSS positioning property and is used as a text wrap for images that are positioned along the web design. Floated elements remain a part of the webpage. Where abolute elements are removed from the flow of a webpage. 

#sidebar {
  float: right;			
}

Used to create web layouts so that it is reflowed to fit, though you want to ensure that it items with text are not affected by the differing margins.

## Clearing the Float
Link: https://css-tricks.com/all-about-floats/
While float sits adjacent to an item, you need to ensure containers arent effected and that is why we use 'clear' this allows it to sit beneath the floats, which helps if you want items to inherit parts of position.

## The Great Collapse
When items are floated in an element (parent) it can callopse on it self as cannot read the specfic height if it only contains nothing but floated elements. If a block element can try to expand and accommodate the floated it could unnatural spacing..

## Techniques for Clearing Floats

- The Empty Dic Methord
<div style="clear: both;"></div>
- The Overflow Method
Setting the overflow CSS property to a parent element so that it expands to contain the floats, clearing succeeding elements.
- The Easy Clearing Method

.clearfix:after { 
   content: "."; 
   visibility: hidden; 
   display: block; 
   height: 0; 
   clear: both;
}

After applying ensure it accommodates older browsers that use different grid layouts as you can space it out.

## Problems with Floats
Floats are too fragile and have bugs where the pushdown effects items that are wider tha a float itself and the page. By overlapping margins  a quick fix is to display: inline so it won't remain a block element. Set a width or height on affected text so it isnt kicked awat from the float. THe bottom margin can be ignored by the children, add it to the parent padding instead.

Fix styling errors by using the parent element (by giving it a height of 0)
Should nexted element not line up.

HTML 

<div class="box-set">
  <figure class="box">Box 1</figure>
  <figure class="box">Box 2</figure>
  <figure class="box">Box 3</figure>
</div>

.box-set,
.box {
  border-radius: 6px;
}
.box-set {
  background: #eaeaed;
}
.box {
  background: #2db34a;
  float: left;
  margin: 1.858736059%;
  padding: 20px 0;
  text-align: center;
  width: 29.615861214%;
}

Again using a closing tag with the decalartion clear: both; but it isnt semantic and depends on how many different floats will need to be cleared as empty elements can stack up without providing any context.

## The Overflow Technique
By setting the overflow to auto within a parent element it will result in an actual height for the parent element.
.box-set {
  overflow: auto;
}
This allows browsers to add scrollbars and help with creating a container for the floated items, especially when the width is 100% of the browser.

However, the added styles or moving nested elements that span outside the parent like box shadows or dropdown menus can be cut off as it lies outside the parent element, causing cropping.

## The Clearfix Technique
Link: https://nicolasgallagher.com/micro-clearfix-hack/

Using a :before pseudo-element to prevent a top margin collapse and :after to clear the floats to ensure visual consistant when the overflow is hidden and when zoom:1 is applied on a parent containing floats. 

Adding the *zoom triggers the hasLayout mechanisim, determines how elements are drawn and bound for their content aswell how elements will iteract with and relate to the element.

.box-set:before,
.box-set:after {
  content: "";
  display: table;
}
.box-set:after {
  clear: both;
}
.box-set {
  *zoom: 1;
}

This prevents cropping that cause it to sit outside the parent element.

## Effectively Containing Floats
Content and your personal preference lets you decide how you will be mixing techniques. A commong practice is to assign a class to the parent element, which includes floats needing to be contained. 

.group:before,
.group:after {
  content: "";
  display: table;
}
.group:after {
  clear: both;
}
.group {
  *zoom: 1;
}

Consider that you must only use one pseudo element per element while the clearfix allows you to refer to :before and :after content it may not let you achieve a desired outcome.

## Position Property
Accepts five different values, each providing a different way.
Link: https://alistapart.com/article/css-positioning-101/
Reminder: static, relative, absolute, fixed and inherit. 
Ensure you are formatting either an block or inline to stack together as part of the noral flow of a website.

Static (default) & Relative (offset from another element)
Using different coordinates to alter your layout>

The position: absolute gives you something removed from the flow, it wont affect or be affected, we can extend what gets offset and placing an image in a parent container as it child.

Inherit is lets the elements influence each other using the values yjay are set by the containers and its parents.

Position Static
How elements are positioned as intended?
HTML
<div class="box-set">
  <figure class="box box-1">Box 1</figure>
  <figure class="box box-2">Box 2</figure>
  <figure class="box box-3">Box 3</figure>
  <figure class="box box-4">Box 4</figure>
</div>

CSS
.box-set {
  background: #eaeaed;
}
.box {
  background: #2db34a;
  height: 80px;
  width: 80px;
}

## Position Relative
Like static accepts the box offset: top, right, bottom and left specfiy how the elements may be positioned and which direction? Yet when elements used absolute or fixed, you need specfy the distamce between the element and the edges of its parent element. 

div class="box-set">
  <figure class="box box-1">Box 1</figure>
  <figure class="box box-2">Box 2</figure>
  <figure class="box box-3">Box 3</figure>
  <figure class="box box-4">Box 4</figure>
</div>

.box-set {
  background: #eaeaed;
}
.box {
  background: #2db34a;
  height: 80px;
  position: relative;
  width: 80px;
}
.box-1 {
  top: 20px;
}
.box-2 {
  left: 40px;
}
.box-3 {
  bottom: -10px;
  right: 20px;
}

Relative still remains in the normal or static, flow of the page. This may overlap, or underlap elements without moving them from their default position. It can cause the boxes to overlap and yet do not push each other in different directions.

## Position Absolute
Upon remoing the elements from the normal flow, in relation to their containing parent, which is usually the body of the page. We can offset it by using it to position the element where we wnt.









