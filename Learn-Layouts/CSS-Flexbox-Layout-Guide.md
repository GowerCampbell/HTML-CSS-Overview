# CSS Flexbox Layout Guide

Everything about hoe the parent element(the flex container) and the child elements(flex items) work. Including, history, demos, patterns and a browser support chart.

## Background
The 'Flexbox' Layout (Flexible Box) module is used to help align and distrubute space among items in a container, even when their size is unknown and/or dynamic (thus flex).

The Flexbox give the container the ability to alter its items width/height (and order) to best fill the available space. Mostly to accommodate media quries(devices/screen sizes) A flex container expands items to fill available free space or shrinks them to prevent overflow. 

The layout is direction-agnostic as opposed to regular layout (block which has verticallly-based and inline which horizontally-based) which doesnt support large or complex applications when it comes to orentation changing, resizig, stretching or shrinking.

Note that the flexbox is for small-scale layouts while grid layout is for larger scale. 


## Basics & Terminology
Flexbox is a module nd has its owns set of properties for the flex container and flex items. The Flex layout is based on "flex-flow directions" 

<img href="https://css-tricks.com/wp-content/uploads/2018/11/00-basic-terminology.svg" alt="The flex layout" />

Items are laid out following either the main axis(from vertical positions; the main-start to main-end) or the cross axis (horiziontal positions: cross start to cross-end.

- <b>main axis</b>: primary axis which flex items are laid out in, not necessaily horizintal, as it depends on the "flex-direction" property
- <b>main-start | main-end</b>: start and end placement in container.
-<b>main size</b>: a flex items width and height(main dimension) dependent on the width or height property
- <b>cross axis</b>: Axis perpendicular to the main axis is the the cross axis and it is dependent on the axis direction.
- <b> cross-start | cross-end: </b> Flex lines are filled with items and placed into the container starting on the cross-start of the flex container and going to the end.
- <b>cross size</b> width or height of a flex item, which is the cross dimension of the items size and dependent on the axis direction.

## Flexbox Properties

### Properties for the Parent (flex container)
<img href="https://css-tricks.com/wp-content/uploads/2018/10/01-container.svg" alt="The flex container" />

#### display
'''
.container {
display: flex; /* or inline-flex */
}
'''
Defines the flex for the direct children.

#### flex direction
'''
.container {
  flex-direction: row | row-reverse | column | column-reverse;
}
'''
Establishes main axis from horizontal rows or vertical columns
row(default): left to right | row-reverse: right to left
column: top to bottom  |  column-reverse: bottom to top

#### flex-wrap
'''
.container {
  flex-wrap: nowrap | wrap | wrap-reverse;
}
'''
Changing how your items fit onto your DOM lines and wrap as needed with this proporty. nowrap(default) items fit on one line | wrap: flex items fit on multiple lines(top to bottom) | wrap-reverse: flex items will wrap onto multiple lines from bottom to top. Link: https://css-tricks.com/almanac/properties/f/flex-wrap/

#### flex-flow
'''
.container {
  flex-flow: column wrap; /* or row nowrap(default) */
}
'''
short-hand for flex-direction & flex-wrap: defines the main and cross axes

#### Justify-content
<img href="https://css-tricks.com/wp-content/uploads/2018/10/justify-content.svg" alt="justify" />

Defines alignment along main or cross axis. 

'''
.container {
  justify-content: flex-start | flex-end | center | space-between | space-around | space-evenly | start | end | left | right ... + safe | unsafe;
}
'''
flex-start: items packed at start | flex-end: items packed at end
start: start of writing-mode direction end: end of writing-mode direction left: or right: edge of the flex container. center: centered along line. space-between: Distributed along the line from start to end. space-around: Not visually even but dependent on the units of space between items and the number of items that make it look even. space-evenly: items are ditrubuted so the spacing between any two items is equal.

Note: Not all browsers will support the space-between proptery (safest are flex-start, flex-end or center.

Including vues + safe or unsafe ensures that the browser does not push an element that it renders off screen.

#### align-items
This defines the defult of items laid out of the cross axis on the current line. Think of it as the "justify-content" 

.container {
  align-items: stretch | flex-start | flex-end | center | baseline | first baseline | last baseline | start | end | self-start | self-end + ... safe | unsafe;
}

- stretch: fill the container (respect min-width/mx-width)
- flex-start/start/self-start: items plced at the start of the croxx axis and it is bout the flex-direction of the flex item.
- flex-end/end/self-end: items are placed at the end of the cross axis, the difference
- center: items are centered in the cross-axis
- baseline: items are aligned such as their baselines lign

Rember the safe & unsafe modifier with the key words and deal with helping wwith aligning elements.

#### align-content 
This aligns a flex container lines when theres is extra space in the cross-axis simular to how justify-content ligns individual items within the main-axis. 

.container {
  align-content: flex-start | flex-end | center | space-between | space-around | space-evenly | stretch | start | end | baseline | first baseline | last baseline + ... safe | unsafe;
}

From the normal to be packed into a contianer, from flex-start/start is packed to the container honoring either the flex-direction or writing-mode direction, which is the same with the flex-end/end. The center and the space-between distribute from the center between. The space-around items are distributed with equal spce around them. The stretch lines strech to take up any remaining space. And again the safe and unsafe are used as modifiers.

##### Note:
This property only takes effect on multi-line flexible containers where flex-wrap is set to either wrap or wrap-reverse and will not reflect align-content.

#### gap, row-gap, column-gap
The gap property controls the space between flex items. It applies that spacing only between items not on the outer edges.

.container {
  display: flex;
  ...
  gap: 10px;
  gap: 10px 20px; /* row-gap column gap */
  row-gap: 10px;
  column-gap: 20px;
}

Conside it as a gutter that suts between items and controls it within the flexbox.

### Properties for the Children (flex items)
<img href="https://css-tricks.com/wp-content/uploads/2018/10/02-items.svg" alt="The flex items" />

#### Order
By default flex items are laid out in source order, though we control the order by the: 

.item {
  order: 5; /* default is 0 */
}

Items with the same order revert to source order.

#### flex-grow

defines the ability for a flex item to grow using a unitless value flex-value from 1 to 2 will take up twice as much space.

.item {
  flex-grow: 4; /* default 0 */
}
Negative numbers are invalid.

#### flex-shrink
defines the ability for a flex item to shrink 
.item {
  flex-shrink: 3; /* default 1 */

}

  Negative numbers are invalid.

  #### flex-basis
This defines the default size of an element before the space is distributed.
The auto keyword means "look at my width or height property from the main-size" using the items content: max-content, min-content and fit-content.
If set to 0 the extra space isnt factored in.

item {
  flex-basis:  | auto; /* default auto */
}
and if set to auto it distribute on its flex-grow value

#### flex 
shorthand for flex-grow, flex-shrink and flex-basis combined. 

.item {
  flex: none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ]
}
Use this than individual properties.

#### align-self
From default alignement to be overridden for 

.item {
  align-self: auto | flex-start | flex-end | center | baseline | stretch;
}

Note: the properties: float, clear and vertical-align has no effect on a flex item

## Prefixing Flexbox
From the vendor creating "old", "tweener" or "new" versions using different propertys or value names.

@mixin flexbox() {
  display: -webkit-box;
  display: -moz-box;
  display: -ms-flexbox;
  display: -webkit-flex;
  display: flex;
}

@mixin flex($values) {
  -webkit-box-flex: $values;
  -moz-box-flex:  $values;
  -webkit-flex:  $values;
  -ms-flex:  $values;
  flex:  $values;
}

@mixin order($val) {
  -webkit-box-ordinal-group: $val;  
  -moz-box-ordinal-group: $val;     
  -ms-flex-order: $val;     
  -webkit-order: $val;  
  order: $val;
}

.wrapper {
  @include flexbox();
}

.item {
  @include flex(1 200px);
  @include order(2);
}

## Examples
Lets start with a very simple example, solving a daily problem from centering with a flexbox. 

.parent {
  display: flex;
  height: 300px; /* Or whatever */
}

.child {
  width: 100px;  /* Or whatever */
  height: 100px; /* Or whatever */
  margin: auto;  /* Magic! */
}

Rely on the auto margin to align the axes now lets add wht we covered:

.flex-container {
  /* We first create a flex layout context */
  display: flex;

  /* Then we define the flow direction 
     and if we allow the items to wrap 
   * Remember this is the same as:
   * flex-direction: row;
   * flex-wrap: wrap;
   */
  flex-flow: row wrap;

  /* Then we define how is distributed the remaining space */
  justify-content: space-around;
}

Using a right-aligned navigation element on the very top of our website, to be centered on medium sized screens and single-columned on small devices

/* Large */
.navigation {
  display: flex;
  flex-flow: row wrap;
  /* This aligns items to the end line on main-axis */
  justify-content: flex-end;
}

/* Medium screens */
@media all and (max-width: 800px) {
  .navigation {
    /* When on medium sized screens, we center it by evenly distributing empty space around items */
    justify-content: space-around;
  }
}

/* Small screens */
@media all and (max-width: 500px) {
  .navigation {
    /* On small screens, we are no longer using row direction but column */
    flex-direction: column;
  }
}

If you want to create a mobiles 3 columns layout with a full width header and footer 

.wrapper {
  display: flex;
  flex-flow: row wrap;
}

/* We tell all items to be 100% width, via flex-basis */
.wrapper > * {
  flex: 1 100%;
}

/* We rely on source order for mobile-first approach
 * in this case:
 * 1. header
 * 2. article
 * 3. aside 1
 * 4. aside 2
 * 5. footer
 */

/* Medium screens */
@media all and (min-width: 600px) {
  /* We tell both sidebars to share a row */
  .aside { flex: 1 auto; }
}

/* Large screens */
@media all and (min-width: 800px) {
  /* We invert order of first sidebar and main
   * And tell the main element to take twice as much width as the other two sidebars 
   */
  .main { flex: 3 0px; }
  .aside-1 { order: 1; }
  .main    { order: 2; }
  .aside-2 { order: 3; }
  .footer  { order: 4; }
}

## FlexBox Tricks
Link https://css-tricks.com/adaptive-photo-layout-with-flexbox/
Link https://css-tricks.com/balancing-on-a-pivot-with-flexbox/
Link https://css-tricks.com/using-flexbox-and-text-ellipsis-together/
link https://css-tricks.com/useful-flexbox-technique-alignment-shifting-wrapping/
link https://css-tricks.com/designing-a-product-page-layout-with-flexbox/
link https://css-tricks.com/flexbox-truncated-text/
Link: https://css-tricks.com/flexbox-and-absolute-positioning/
Link: https://css-tricks.com/filling-space-last-row-flexbox/

## Browser Support
Desktop :21 :28 :11 :12 :6.1
Mobile/Tablet: :139 :142 :4.4 :7.0-7.1

## Bugs
Flexbox has bugs and its open sources to track them all: https://github.com/philipwalton/flexbugs

## Related Propeties

align-content
https://css-tricks.com/almanac/properties/a/align-content/

align-items
https://css-tricks.com/almanac/properties/a/align-items/

align-self
https://css-tricks.com/almanac/properties/a/align-self/

column-gap
https://css-tricks.com/almanac/properties/g/gap/column-gap/

display
https://css-tricks.com/almanac/properties/d/display/

gap
https://css-tricks.com/almanac/properties/g/gap/

justify-items
https://css-tricks.com/almanac/properties/j/justify-items/

flex
https://css-tricks.com/almanac/properties/f/flex/

flex-basis
https://css-tricks.com/almanac/properties/f/flex-basis/

flex-direction
https://css-tricks.com/almanac/properties/f/flex-direction/

flex-flow
(https://css-tricks.com/almanac/properties/f/flex-flow/)

flex-grow
https://css-tricks.com/almanac/properties/f/flex-grow/

flex-shrink
https://css-tricks.com/almanac/properties/f/flex-shrink/

flex-wrap
https://css-tricks.com/almanac/properties/f/flex-wrap/

justify-content
https://css-tricks.com/almanac/properties/j/justify-content/

justify-self
https://css-tricks.com/almanac/properties/j/justify-self/

row-gap
https://css-tricks.com/almanac/properties/g/gap/row-gap/

## More Informtion
- https://www.w3.org/TR/css-flexbox-1/
- https://www.digitalocean.com/community/cheatsheets/css-flexbox?utm_medium=content_acq&utm_source=css-tricks&utm_campaign=&utm_content=awareness_bestsellers
- https://www.digitalocean.com/community/tutorials/css-centering-using-flexbox?utm_medium=content_acq&utm_source=css-tricks&utm_campaign=&utm_content=awareness_bestsellers
- https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Flexbox
- https://www.smashingmagazine.com/2018/10/flexbox-use-cases/

