# Transitions & Animations

Using HTML & CSS to write behaviors for transitions and animations without JavaScript or Flash. CSS3 transitions can change an element's state when hovered, focused, active, or targeted. CSS3 animations allow for more complex appearance and behavior changes using multiple keyframes set at various points of a transition.

-----

## Transitions (like butter 🧈)

Transitions smooth out value changes from user interactions over a specified duration. They are often triggered by pseudo-classes like `:hover`, `:focus`, `:active`, and `:target`.

The core transition-related properties are:

  * `transition-property`
  * `transition-duration`
  * `transition-timing-function`
  * `transition-delay`

For example, to change an element's background color over 1 second:

```css
.box {
  background: #2db34a;
  transition-property: background;
  transition-duration: 1s;
  transition-timing-function: linear;
}
.box:hover {
  background: #ff7b29;
}
```

**Helpful Link:** [Understanding CSS3 Transitions](https://alistapart.com/article/understanding-css3-transitions/)

### Vendor Prefixes

To ensure transitions work across different browsers, you should include vendor prefixes:

```css
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
```

### Transition Properties

The `transition-property` determines exactly which CSS properties will be animated. To transition multiple properties, you can list them separated by a comma. Not all properties can be transitioned; they must have an identifiable halfway point.

A few transitionable properties include:
`background-color`, `background-position`, `border-color`, `border-width`, `color`, `font-size`, `height`, `left`, `margin`, `opacity`, `padding`, `right`, `top`, `width`, `z-index`.

```css
.box {
  background: #2db34a;
  border-radius: 6px;
  transition-property: background, border-radius;
  transition-duration: 1s;
  transition-timing-function: linear;
}
.box:hover {
  background: #ff7b29;
  border-radius: 50%;
}
```

### Transition Duration

This property sets the length of the transition using seconds (`s`) or milliseconds (`ms`). You can set different durations for each property, and the order corresponds to the order in `transition-property`.

```css
.box {
  background: #2db34a;
  border-radius: 6px;
  transition-property: background, border-radius;
  transition-duration: .2s, 1s; /* background takes 0.2s, border-radius takes 1s */
  transition-timing-function: linear;
}
.box:hover {
  background: #ff7b29;
  border-radius: 50%;
}
```

### Transition Timing Function

The `transition-timing-function` property sets the speed curve of the transition.

  * **linear**: constant speed.
  * **ease-in**: starts slowly, then speeds up.
  * **ease-out**: starts quickly, then slows down.
  * **ease-in-out**: starts slowly, speeds up in the middle, then slows down at the end.

You can also define a custom curve with `cubic-bezier(x1, y1, x2, y2)` or use step functions like `steps(number_of_steps, direction)`.

```css
.box {
  background: #2db34a;
  border-radius: 6px;
  transition-property: background, border-radius;
  transition-duration: .2s, 1s;
  transition-timing-function: linear, ease-in; /* linear for background, ease-in for border-radius */
}
.box:hover {
  background: #ff7b29;
  border-radius: 50%;
}
```

### Transition Delay

This property sets a time to wait before the transition begins.

```css
.box {
  background: #2db34a;
  border-radius: 6px;
  transition-property: background, border-radius;
  transition-duration: .2s, 1s;
  transition-timing-function: linear, ease-in;
  transition-delay: 0s, 1s; /* No delay for background, 1s delay for border-radius */
}
.box:hover {
  background: #ff7b29;
  border-radius: 50%;
}
```

### Shorthand `transition` Property

You can combine all the transition properties into the shorthand `transition` property. The order of values is **property**, **duration**, **timing-function**, and **delay**.

```css
.box {
  background: #2db34a;
  border-radius: 6px;
  transition: background .2s linear, border-radius 1s ease-in 1s;
}
.box:hover {
  background: #ff7b29; /* Typo in original notes corrected: should be background, not color */
  border-radius: 50%;
}
```

### Transition Examples

#### Button Press Effect

**HTML**

```html
<button>Awesome Button</button>
```

**CSS**

```css
button {
  border: 0;
  background: #0087cc;
  border-radius: 4px;
  box-shadow: 0 5px 0 #006599;
  color: #fff;
  cursor: pointer;
  font: inherit;
  margin: 0;
  outline: 0;
  padding: 12px 20px;
  transition: all .1s linear;
}
button:active {
  box-shadow: 0 2px 0 #006599;
  transform: translateY(3px);
}
```

#### Card Flip Effect

**HTML**

```html
<div class="card-container">
  <div class="card">
    <div class="side">...</div>
    <div class="side back">...</div>
  </div>
</div>
```

**CSS**

```css
.card-container {
  height: 150px;
  perspective: 600;
  position: relative;
  width: 150px;
}
.card {
  height: 100%;
  position: absolute;
  transform-style: preserve-3d;
  transition: all 1s ease-in-out;
  width: 100%;
}
.card:hover {
  transform: rotateY(180deg);
}
.card .side {
  backface-visibility: hidden;
  height: 100%;
  position: absolute;
  width: 100%;
}
.card .back {
  transform: rotateY(180deg);
}
```

-----

## Animations 🎬

While transitions are great for simple state changes, animations provide much more control over multiple stages of an effect.

**Helpful Link:** [The Guide To CSS Animation](https://www.smashingmagazine.com/2011/09/the-guide-to-css-animation-principles-and-examples/)

### Animation `@keyframes`

The `@keyframes` rule is where you define the stages of your animation. You give the animation a name and set CSS properties at specific points (breakpoints) using percentages.

```css
@keyframes slide {
  0% {
    left: 0;
    top: 0;
  }
  50% {
    left: 244px;
    top: 100px;
  }
  100% {
    left: 488px;
    top: 0;
  }
}
```

Like transitions, keyframes also need vendor prefixes (`@-webkit-keyframes`, `@-moz-keyframes`, etc.).

### Applying Animations

Once keyframes are defined, you apply them to an element using animation properties.

  * `animation-name`: The name you defined in `@keyframes`.
  * `animation-duration`: How long the animation takes.
  * `animation-timing-function`: The speed curve of the animation (e.g., `linear`, `ease-in-out`).
  * `animation-delay`: A pause before the animation starts.

**HTML Example**

```html
<div class="stage">
  <figure class="ball"></figure>
</div>
```

**CSS Example**

```css
/* Keyframes defined above */

.stage {
  height: 150px;
  position: relative;
}
.ball {
    background: #0087cc; /* Added for visibility */
    border-radius: 50%; /* Added for visibility */
    height: 50px;
    position: absolute;
    width: 50px;
}
.stage:hover .ball {
  animation-name: slide;
  animation-duration: 2s;
  animation-timing-function: ease-in-out;
  animation-delay: .5s;
}
```

### Customizing Animations

You can further customize an animation's behavior.

  * `animation-iteration-count`: The number of times the animation should run. Use `infinite` for a continuous loop.
  * `animation-direction`: Controls how the animation plays through its cycle.
      * `normal`: Forward (0% to 100%).
      * `reverse`: Backward (100% to 0%).
      * `alternate`: Forward, then backward.
      * `alternate-reverse`: Backward, then forward.
  * `animation-play-state`: Allows you to `pause` or resume (`running`) an animation. This is often used with pseudo-classes like `:active` or `:hover`.
  * `animation-fill-mode`: Defines what styles are applied before and after the animation runs.
      * `none`: Default. No styles are applied outside the animation's execution time.
      * `forwards`: The element retains the styles from the last keyframe after the animation finishes.
      * `backwards`: The element gets the styles from the first keyframe before the animation starts (during any delay).
      * `both`: Applies the rules for both `forwards` and `backwards`.

<!-- end list -->

```css
.stage:hover .ball {
  animation-name: slide;
  animation-duration: 2s;
  animation-timing-function: ease-in-out;
  animation-delay: .5s;
  animation-iteration-count: infinite;
  animation-direction: alternate;
  animation-fill-mode: forwards;
}
.stage:active .ball {
  animation-play-state: paused;
}
```

### Shorthand `animation` Property

All animation properties can be combined into the shorthand `animation` property. The order is generally:
`name` `duration` `timing-function` `delay` `iteration-count` `direction` `fill-mode` `play-state`.

```css
.stage:hover .ball {
  animation: slide 2s ease-in-out .5s infinite alternate;
}
.stage:active .ball {
  animation-play-state: paused;
}
```

**Helpful Link:** [MDN: Using CSS animations](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_animations/Using_CSS_animations)

-----

## Test Your Knowledge 🤔

\<details\>
\<summary\>What is the main difference between a CSS transition and a CSS animation?\</summary\>
\<p\>Transitions are used to animate an element from a starting state to an ending state, typically triggered by a pseudo-class like \<code\>:hover\</code\>. Animations are more powerful and allow for multi-step sequences defined in a \<code\>@keyframes\</code\> rule, giving you more control over the intermediate steps of the effect.\</p\>
\</details\>

\<details\>
\<summary\>What are the four main properties used to define a transition?\</summary\>
\<p\>The four properties are: \<code\>transition-property\</code\>, \<code\>transition-duration\</code\>, \<code\>transition-timing-function\</code\>, and \<code\>transition-delay\</code\>.\</p\>
\</details\>

\<details\>
\<summary\>What is the correct value order for the shorthand \<code\>transition\</code\> property?\</summary\>
\<p\>The order is: property, duration, timing-function, and delay. For example: \<code\>transition: background-color 1s ease-in 0.5s;\</code\>\</p\>
\</details\>

\<details\>
\<summary\>What is the purpose of the \<code\>@keyframes\</code\> rule in CSS?\</summary\>
\<p\>The \<code\>@keyframes\</code\> rule is used to define the stages (or breakpoints) of an animation sequence. You assign a name to the animation and specify the CSS styles for different points in time, using percentages from 0% (the start) to 100% (the end).\</p\>
\</details\>

\<details\>
\<summary\>How can you make a CSS animation repeat forever?\</summary\>
\<p\>By setting the \<code\>animation-iteration-count\</code\> property to the value \<code\>infinite\</code\>.\</p\>
\</details\>

\<details\>
\<summary\>What does the \<code\>animation-direction\</code\> value \<code\>alternate\</code\> do?\</summary\>
\<p\>It makes the animation play forwards on odd-numbered iterations (1, 3, 5, etc.) and backwards on even-numbered iterations (2, 4, 6, etc.).\</p\>
\</details\>

\<details\>
\<summary\>What is the purpose of the \<code\>animation-fill-mode\</code\> property?\</summary\>
\<p\>It determines how an element is styled before the animation starts and/or after it ends. For example, \<code\>forwards\</code\> will make the element retain the styles from its final keyframe.\</p\>
\</details\>
