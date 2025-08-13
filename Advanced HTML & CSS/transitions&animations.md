# Transitions & Animations
Writing behaviors for transitions and animations using HTML & CSS without JavaScript or Flash. Using CSS3 transition too to change the state of the element when it is hovered, focused or when it is made active when targeted.

Animations within CSS3 that allows for appearance and behavior using multiple keyframes, set at multople points of transition.

## Transitions (butter)
Smoothing out value changes by interactions over a specfied duration.
Link: https://alistapart.com/article/understanding-css3-transitions/
Determine the styles using psuido=classes like :hover, :focus, :active and :target

Transition related properties allow 

transition-property: linear, all, or 2s
transition-duration
trasition-timing-function
transition-delay

Changing its background color over 1 second
.box {
  background: #2db34a;
  transition-property: background;
  transition-duration: 1s;
  transition-timing-function: linear;
}
.box:hover {
  background: #ff7b29;
}

## Vendor Prefixs
To use across browsers/vendor consider belows layout:

.box {
    background: #2db34a;
    -webkit-transition-property: background;
       -moz-transition-property: background;
         -o-transition-property: background;
            transition-property: background;
    -webkit-transition-duration: 1s;
       -moz-transition-duration: 1s;
         -o-transition-duration: 1s;
            transition-duration: 1s;
    -webkit-transition-timing-function: linear;
       -moz-transition-timing-function: linear;
         -o-transition-timing-function: linear;
            transition-timing-function: linear;
}
.box:hover {
  background: #ff7b29;
}

## Transitional Property
Determines exactly what properties will be altered in conjunction with other properties, thir different states and lets us set for example, the background property, be used over the duration of 1 sec and it is done linear. 

.box {
    background: #2db34a;
    border-radius: 6px
    transition-property: background, border-radius;
    transition-duration: 1s;
    transition-timing-function: linear;
  }
  .box:hover {
    background: #ff7b29;
    border-radius: 50%;
  }

If multiple properties need to be trasitioned, use comma... on 'transition-property'

## Transitional Properties
Not all properties may be transitioned, only those with a halfwat ponit 
Here are a few:
background-color background-position border-color border-width border-spacing bottom clip color crop font-size font-weight height left letter-spacing line-height margin max-height max-width min-height min-width opacity outline-color outline-offset outline-width padding right text-indent text-shadow top vertical-align visibility width word-spacing z-index

## Transition Duration
General timing values between seconds (s) and milliseconds (ms) consider fractional aswell (floats) You can set multiple durations or each property through the syntax. The order is based on each property used... 

.box {
  background: #2db34a;
  border-radius: 6px;
  transition-property: background, border-radius;
  transition-duration: .2s, 1s;
  transition-timing-function: linear;
}
.box:hover {
  background: #ff7b29;
  border-radius: 50%;

## Transition Timing

Here 'transition-timing-function' proprty is used to set the speed in which a transition will move: linear (constant speed), ease-in(starts slowly, then speeds up), ease-out(starts quickly, then slows down) and ease-in-out(starts slowly, speeds up in the middle and then slows down at the end)

Each timing has a cubic-bezier curve  and is set specfically by 
cubic-bezier(x1, y1, x2, y2) value. Additionl values include step-start, step-stop and uniqully identify its steos by steps(number_of_steps, direction) These are timing function and helps you use a more controlled transition

.box {
  background: #2db34a;
  border-radius: 6px;
  transition-property: background, border-radius;
  transition-duration: .2s, 1s;
  transition-timing-function: linear, ease-in;
}
.box:hover {
  background: #ff7b29;
  border-radius: 50%;
}

## Transition Delay
Delays the transition by a time value before it can happen.

.box {
  background: #2db34a;
  border-radius: 6px
  transition-property: background, border-radius;
  transition-duration: .2s, 1s;
  transition-timing-function: linear, ease-in;
  transition-delay: 0s, 1s;
}
.box:hover {
  background: #ff7b29;
  border-radius: 50%;
}

## Shorthand Transition
Using just 'transition' it is also capable of supporting all the different properties and values

Including transition-property, transition-duration, transition-timing-function, and lastly transition-delay

.box {
  background: #2db34a;
  border-radius: 6px;
  transition: background .2s linear, border-radius 1s ease-in 1s;
}
.box:hover {
  color: #ff7b29;
  border-radius: 50%;
}




