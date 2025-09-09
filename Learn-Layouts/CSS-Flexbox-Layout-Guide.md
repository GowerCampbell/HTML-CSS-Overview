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

From the normal to be packed into a contianer, from flex-start/start is packed to the container honoring either the flex-direction or writing-mode direction, which is the same with the flex-end/end. The center 

##### Note:
This property only takes effect on multi-line flexible containers where flex-wrap is set to either wrap or wrap-reverse and will not reflect align-content.

### Properties for the Children (flex items)
<img href="https://css-tricks.com/wp-content/uploads/2018/10/02-items.svg" alt="The flex items" />


