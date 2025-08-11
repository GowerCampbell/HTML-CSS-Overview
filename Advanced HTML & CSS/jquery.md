

# JavaScript & jQuery Cheatsheet 

A collection of notes and code snippets for quick reference on JavaScript and jQuery fundamentals. Over 92% of websites use JavaScript, and of those, about 63% use the jQuery library. Learning both is a powerful combination for building interactive web experiences.

-----

## JavaScript Fundamentals 

JavaScript provides the behavior and interactivity for a web page, working alongside **HTML** (structure) and **CSS** (appearance).

### **Setup**

To include JavaScript in your HTML file, save your code in an external file with a `.js` extension. Link it using the `<script>` element right before the closing `</body>` tag. This ensures the HTML content is loaded before the script runs.

```html
...
    <script src="script.js"></script>
  </body>
</html>
```

-----

### **Values & Variables**

  * **Values** are the fundamental pieces of information in JavaScript (e.g., strings, numbers, booleans, `null`, `undefined`).
  * **Variables** are containers for storing and reusing these values.

#### **Declaring Variables**

Declare a variable using the `var` keyword, a name, an equals sign `=`, and a value, ending with a semicolon `;`.

**Naming Rules:**

  * Must start with a letter, underscore `_`, or dollar sign `$`.
  * Cannot start with a number or contain a hyphen `-`.
  * Are **case-sensitive**.
  * The convention is **camelCase** (e.g., `myVariableName`).

<!-- end list -->

```javascript
var theStarterLeague = 125;
var foodTruck = 'Coffee'; // camelCase is preferred
var mixtape01 = true;
var vinyl = ['Miles Davis', 'Frank Sinatra', 'Ray Charles'];
```

-----

### **Statements**

A JavaScript program is a sequence of statements executed by the browser. Each statement is like a command.

```javascript
console.log(polaroid);
return('bicycle lane');
alert('Congratulations, you ' + outcome);
```

-----

### **Functions**

Functions are reusable blocks of code that perform a specific task. They are defined with the `function` keyword, a name, parentheses `()`, and the code to be executed inside curly braces `{}`. They can optionally accept arguments.

```javascript
function greetUser(name) {
  alert('Hello, ' + name + '!');
}
```

-----

### **Arrays**

An array is a special variable that can hold a list of multiple values. Array items are **zero-indexed** (the first item is at index `0`) and enclosed in square brackets `[]`.

```javascript
// An array of strings
var schoolLocations = ['Austin', 'Chicago', 'Portland'];

// Accessing an item
console.log(schoolLocations[1]); // Outputs: 'Chicago'
```

-----

### **Objects**

Objects are collections of key-value pairs, similar to dictionaries in other languages. They are foundational to JavaScript.

```javascript
// Object Literal
var school = {
  name: 'The Starter League',
  location: 'Merchandise Mart',
  studentCount: 120,
  teachers: ['Jeff', 'Raghu', 'Carolyn', 'Shay']
};

// Accessing a value
console.log(school.name); // Outputs: 'The Starter League'
```

> **Tip:** You can execute JavaScript directly in your browser's developer console for quick testing.

-----

## Getting Started with jQuery 

jQuery is a fast, small, and feature-rich JavaScript library created by John Resig. It simplifies things like HTML document traversal and manipulation, event handling, and animation.

[**Course Link: 30 Days to Learn jQuery**](https://code.tutsplus.com/30-days-to-learn-jquery--CRS-41c)

### **Setup and Installation**

Because jQuery is a library, you must include it in your page *before* your custom scripts. It's best practice to use a **minified** version from a **Content Delivery Network (CDN)** for better performance and caching.

Place the script tags just before the closing `</body>` tag.

```html
    <script src="//ajax.googleapis.com/ajax/libs/jquery/1.9.0/jquery.min.js"></script>
    <script src="script.js"></script>
  </body>
</html>
```

> **Note:** The protocol-less URL `//ajax.googleapis.com/...` allows the browser to request the file using either HTTP or HTTPS, matching the protocol of your page.

### **The Document Ready Event**

To ensure your code doesn't run until the HTML document (**DOM**) is fully loaded and ready, wrap all your jQuery code in a `ready` event handler.

```javascript
// script.js

// You can use either $() or jQuery()
$(document).ready(function() {
  // All your jQuery code goes here!
});
```

-----

## jQuery Core Concepts 

### **Selectors**

jQuery uses CSS-style selectors to find and select HTML elements. The selector is passed as a string to the jQuery object `$()`.

**Common Selector Examples:**

  * `$('.feature');` - Selects all elements with the class `feature`.
  * `$('li strong');` - Selects all `<strong>` elements inside `<li>` elements.
  * `$('em, i');` - Selects all `<em>` and `<i>` elements.
  * `$('a[target="_blank"]');` - Selects all `<a>` elements with a `target` attribute of `_blank`.
  * `$('p:nth-child(2)');` - Selects every `<p>` that is the second child of its parent.

[**See All Selectors in the API Docs**](https://api.jquery.com/category/selectors/)

#### **The `this` Keyword**

Inside a jQuery event handler, `this` refers to the specific DOM element that triggered the event. To use jQuery methods on it, wrap it in `$()` like so: `$(this)`.

```javascript
$('div').on('click', function() {
  // 'this' refers to the specific div that was clicked
  $(this).hide();
});
```

-----

### **Traversing the DOM**

Traversing means moving through the DOM tree to find related elements. jQuery provides many methods for moving up, down, and sideways from a selected element.

**Chaining Methods:**
You can chain multiple methods together to perform a sequence of actions on a selection.

```javascript
// Find all divs, exclude those with class 'type' or 'collection', then select their parents.
$('div').not('.type, .collection').parent();
```

**Traversing Categories:**

  * **Filtering:** Narrow down the selection (e.g., `.filter()`, `.not()`, `.first()`, `.last()`, `.eq()`).
  * **Tree Traversal:** Move around the DOM (e.g., `.children()`, `.parent()`, `.parents()`, `.siblings()`, `.find()`, `.next()`).
  * **Miscellaneous:** `.add()`, `.end()`, `.contents()`.

[**See All Traversing Methods in the API Docs**](https://api.jquery.com/category/traversing/)

-----

### **DOM Manipulation**

Once you've selected elements, you can manipulate their content, attributes, and styles.

[**See All Manipulation Methods in the API Docs**](https://api.jquery.com/category/manipulation/)

#### **Getters and Setters**

Many jQuery methods work as both "getters" (retrieving a value) and "setters" (changing a value).

  * **Get:** Call the method with no arguments.
  * **Set:** Call the method with an argument.

<!-- end list -->

```javascript
// GET the value of the 'alt' attribute
var altText = $('img').attr('alt');

// SET the value of the 'alt' attribute
$('img').attr('alt', 'A wild kangaroo');
```

#### **Manipulating Attributes & Classes**

```javascript
// Add a class to all even-numbered list items
$('li:even').addClass('even-item');

// Remove all classes from any paragraph
$('p').removeClass();

// Add or remove a class on each click
$('div').toggleClass('active');
```

*Other methods include:* `.hasClass()`, `.removeAttr()`, `.prop()`, `.removeProp()`, `.val()`.

#### **Manipulating Styles**

Use the `.css()` method to get or set CSS properties.

```javascript
// Set a single property
$('h1 span').css('font-size', 'normal');

// Set multiple properties using an object
$('div').css({
  fontSize: '13px',
  background: '#f60'
});
```

*Other methods include:* `.height()`, `.width()`, `.position()`, `.offset()`.

#### **Manipulating the DOM Structure**

You can add, remove, and alter the elements themselves.

```javascript
// Add a new h3 inside the beginning of every <section>
$('section').prepend('<h3>Featured</h3>');

// Add a new em element just after any link that opens in a new window
$('a[target="_blank"]').after('<em> (opens new window)</em>');

// Replace the text content of any h1
$('h1').text('Hello World');
```

*Other methods include:* `.append()`, `.before()`, `.remove()`, `.empty()`, `.html()`.

-----

## Events & Effects 

### **Handling Events**

Event handlers are functions that run when a user interacts with the page (e.g., clicking, hovering, typing). The `.on()` method is the recommended way to handle events as it's flexible and works with elements added to the page dynamically.

```javascript
// When any <li> is clicked, add the 'saved-item' class to it
$('li').on('click', function(event) {
  $(this).addClass('saved-item');
});
```

[**See All Events in the API Docs**](https://api.jquery.com/category/events/)

-----

### **Using Effects**

jQuery provides simple methods for creating common animations like showing, hiding, fading, and sliding content.

[**See All Effects in the API Docs**](https://api.jquery.com/category/effects/)

#### **Effect Options (Duration, Easing, Callback)**

Most effect methods can accept optional arguments:

1.  **Duration:** How long the animation takes. Can be a keyword (`'slow'`, `'fast'`) or a number in milliseconds (e.g., `500`).
2.  **Easing:** The speed of the animation's progression. Defaults are `swing` (eases in and out) and `linear` (constant speed). For more options, use a plugin like [jQuery UI](https://jqueryui.com/).
3.  **Callback:** A function that runs *after* the effect is complete.

<!-- end list -->

```javascript
$('.error').show('slow', 'linear', function() {
  // This runs after the .error element has finished showing
  console.log('Animation complete!');
});
```

#### **Common Effect Methods**

  * **Basic:** `.hide()`, `.show()`, `.toggle()`
  * **Fading:** `.fadeIn()`, `.fadeOut()`, `.fadeTo()`, `.fadeToggle()`
  * **Sliding:** `.slideDown()`, `.slideUp()`, `.slideToggle()`
  * **Custom:** `.animate()`, `.stop()`, `.delay()`, `.queue()`

-----

### **Demos**

#### **Demo: Fade & Remove Notice**

Using a callback is crucial for actions that should only happen after an animation finishes.
**HTML:**

```html
<div class="notice-warning">
  <div class="notice-close">&#215;</div>
  <strong>Warning!</strong> I’m about to lose my cool.
</div>
```

**JavaScript:**

```javascript
$('.notice-close').on('click', function(event) {
  // Fade the notice out, and once it's invisible, remove it from the DOM.
  $(this).closest('.notice-warning').fadeOut('slow', function() {
    $(this).remove();
  });
});
```

#### **Demo: Sliding Panel**

**HTML:**

```html
<div class="panel">
  <div class="panel-stage" style="display: none;">Content goes here...</div>
  <a href="#" class="panel-tab">Open <span>&#9660;</span></a>
</div>
```

**JavaScript:**

```javascript
$('.panel-tab').on('click', function(event){
  event.preventDefault();
  var panelTab = $(this); // Store reference to the tab

  $('.panel-stage').slideToggle('slow', function(){
    if ($(this).is(':visible')) {
      panelTab.html('Close <span>&#9650;</span>');
    } else {
      panelTab.html('Open <span>&#9660;</span>');
    }
  });
});
```

#### **Demo: Content Tabs**

**HTML:**

```html
<ul class="tabs-nav">
  <li><a href="#tab-1">Features</a></li>
  <li><a href="#tab-2">Details</a></li>
</ul>
<div class="tabs-stage">
  <div id="tab-1">...Content for tab 1...</div>
  <div id="tab-2">...Content for tab 2...</div>
</div>
```

**JavaScript:**

```javascript
// Show the first tab by default
$('.tabs-stage div').hide();
$('.tabs-stage div:first').show();
$('.tabs-nav li:first').addClass('tab-active');

// Change tab class and display content on click
$('.tabs-nav a').on('click', function(event){
  event.preventDefault();
  $('.tabs-nav li').removeClass('tab-active');
  $(this).parent().addClass('tab-active');
  $('.tabs-stage div').hide();
  $($(this).attr('href')).show();
});
```

-----

## Resources 

  * [**JavaScript for Cats**](https://jsforcats.com/): A gentle introduction to JavaScript.
  * [**MDN JavaScript Guide**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Language_overview): Comprehensive and detailed documentation from Mozilla.<p>**Examples:**</p>
```javascript
log(polaroid);
return('bicycle lane');
alert('Congratulations, you ' + outcome);
```
</details>

## Functions

<details>
<summary>What are functions and how do I define one?</summary>
<p>Functions perform a set of scripted behaviors. They are saved for later and, depending on the function, they may even accept different arguments.</p>
<p>A function is defined by using the `function` keyword, followed by a name and parentheses `()`. The code to be executed is placed within enclosed curly braces `{}`.</p>
</details>

## Arrays

<details>
<summary>What's an array and why is it useful?</summary>
<p>An array is a way to store a list of items, or values. Arrays are helpful for many reasons, one being the ability to be traversed with different methods or operators. Depending on the situation, arrays can be used to store and return a variety of different values.</p>
<p>Arrays are set within square brackets `[]` with comma-separated items. The items start at index 0 and increase from there.</p>
</details>

## Objects

<details>
<summary>What is a JavaScript object?</summary>
<p>JavaScript is built on the foundation of objects (which are like a dictionary), a collection of keys and values.</p>
<p>**Object Example:**</p>
```javascript
// Object
var school = {
  name: 'The Starter League',
  location: 'Merchandise Mart',
  students: 120,
  teachers: ['Jeff', 'Raghu', 'Carolyn', 'Shay']
};
```
<p>**Array for Comparison:**</p>
```javascript
// Array
var school = ['Austin', 'Chicago', 'Portland'];
```
<p>I need to remember I can use the browser's console to run JavaScript.</p>
</details>

# jQuery Intro

<details>
<summary>What is jQuery?</summary>
<p>It's an open-source JavaScript library written by John Resig that simplifies the interaction between HTML, CSS, and JavaScript.</p>
<p>**Course Link:** <a href="https://code.tutsplus.com/30-days-to-learn-jquery--CRS-41c" target="_blank">30 Days to Learn jQuery</a></p>
</details>

## Getting Started with jQuery

<details>
<summary>How do I get started with jQuery on my page?</summary>
<p>I need to set a `<script>` element to reference it before closing the `</body>` tag. Because jQuery is its own library, it is best to keep it separate from all other JavaScript I'm writing.</p>
</details>

<details>
<summary>What should I consider when referencing jQuery (minified vs CDN)?</summary>
<p>I must consider if I want to use the **minified** version or the **uncompressed** version. Also, I should consider using a content delivery network (**CDN**) such as Google Hosted Libraries, especially for a live production environment. Using the minified version from a CDN reduces loading time and has potential caching benefits.</p>
<p>**Google Hosted Libraries:** <a href="https://developers.google.com/speed/libraries" target="_blank">https://developers.google.com/speed/libraries</a></p>
```html
<script src="//ajax.googleapis.com/ajax/libs/jquery/1.9.0/jquery.min.js"></script>
<script src="script.js"></script>
```
<p>All custom and handwritten JavaScript & jQuery should be written in `script.js`, as it is placed after jQuery so it may reference keywords in the jQuery library. Notice there is no `https:` within the Google CDN to allow for both http and https connections. Without a web server, `http:` will need to be included to locate the file on the system's local drive.</p>
</details>

## The jQuery Object & Document Ready

<details>
<summary>How do I call the jQuery library in my JavaScript file?</summary>
<p>I can use either `$();` or `jQuery();`. This allows me to set up my files.</p>
</details>

<details>
<summary>Why do I need to wait for the DOM to be ready, and how do I do it in jQuery?</summary>
<p>I'm forced to wait for the Document Object Model (DOM) to finish loading. jQuery has a ready event, `.ready()`, which ensures that all of my custom functions using jQuery will not be executed until the page has loaded and the DOM is ready.</p>
```javascript
$(document).ready(function(event){
  // jQuery code
});
```
</details>

## Selectors

<details>
<summary>How does jQuery select elements, and can I see some examples?</summary>
<p>Mimicking CSS, jQuery can select multiple elements from HTML. Invoking the jQuery object `$()` allows me to contain a selector that will return the DOM node(s) to manipulate, as it falls within the parentheses and quotes `$('...')`.</p>
<p>**Selector Examples:**</p>
<ul>
<li>`$('.feature');` // Class selector</li>
<li>`$('li strong');` // Descendant selector</li>
<li>`$('em, i');` // Multiple selector</li>
<li>`$('a[target="_blank"]');` // Attribute selector</li>
<li>`$('p:nth-child(2)');` // Pseudo-class selector</li>
</ul>
<p>**Selector API Link:** <a href="https://api.jquery.com/category/selectors/" target="_blank">https://api.jquery.com/category/selectors/</a></p>
</details>

<details>
<summary>What does the 'this' keyword do inside a jQuery event?</summary>
<p>I need to consider how it can work within a function, using it to select the element referenced inside the original selector. When an event is raised, using `this` as an operator refers to the specific element that was selected in the current handler.</p>
```javascript
$('div').click(function(event){
  $(this); // 'this' refers to the specific div that was clicked
});
```
</details>

## Traversing

<details>
<summary>What are jQuery Selection Filters and why might they be slow?</summary>
<p>These are extensions to CSS3 and provide control over selecting an element and its relatives. For example: `$('div:has(strong)');`. Used within the selector, however, they are not native to the DOM and can be a bit slow. I should consider using the `:filter()` method instead for traversing.</p>
<p>**Filter Link:** <a href="https://api.jquery.com/category/selectors/jquery-selector-extensions/" target="_blank">jQuery Selector Extensions</a></p>
</details>

<details>
<summary>What is traversing and how do I do it?</summary>
<p>Sometimes CSS selectors alone do not cut it and I need a little more detailed control. Fortunately, jQuery provides a handful of methods for moving up and down the DOM tree, filtering and selecting elements as necessary.</p>
<p>To get started with filtering elements inside the DOM, a general selection needs to be made from which I will traverse relatively. This allows me to find all `div` elements but then exclude the ones chosen by the `.not()` method.</p>
```javascript
$('div').not('.type, .collection');
```
</details>

<details>
<summary>How does chaining methods work?</summary>
<p>By using the dot `.` to control which methods are called on a selection. Consider this use: `$('div').not('.type, .collection').parent();`. Combined together, this will only select the parent elements of `div` elements that do not have a class of 'type' or 'collection'.</p>
</details>

<details>
<summary>What are the three categories of traversing methods?</summary>
<p>The jQuery traversing methods fall into three categories:</p>
<ul>
<li><b>Filtering:</b> `.eq()`, `.filter()`, `.first()`, `.has()`, `.is()`, `.last()`, `.map()`, `.not()`, `.slice()`</li>
<li><b>Miscellaneous Traversing:</b> `.add()`, `.andSelf()`, `.contents()`, `.end()`</li>
<li><b>DOM Tree Traversal:</b> `.children()`, `.closest()`, `.find()`, `.next()`, `.nextAll()`, `.nextUntil()`, `.offsetParent()`, `.parent()`, `.parents()`, `.parentsUntil()`, `.prev()`, `.prevAll()`, `.prevUntil()`, `.siblings()`</li>
</ul>
<p><b>Traversing Methods Link:</b> <a href="https://api.jquery.com/category/traversing/" target="_blank">https://api.jquery.com/category/traversing/</a></p>
</details>

## Manipulation

<details>
<summary>What are the main ways I can manipulate elements with jQuery?</summary>
<p>After selecting and traversing elements in the DOM, I can use the library to manipulate these elements either by reading, adding, or changing attributes or styles. Additionally, elements can be altered, such as changing their placement, removing them, adding new elements, and so forth.</p>
<p><b>Manipulation Link:</b> <a href="https://api.jquery.com/category/manipulation/" target="_blank">https://api.jquery.com/category/manipulation/</a></p>
</details>

<details>
<summary>How do I get and set information with jQuery?</summary>
<p>There are two directives: getting information and setting it. This revolves around using a selector to determine what information is to be retrieved or changed.</p>
```javascript
// Gets the value of the alt attribute
$('img').attr('alt');

// Sets the value of the alt attribute
$('img').attr('alt', 'Wild kangaroo');
```
</details>

<details>
<summary>How can I manipulate attributes?</summary>
<p>I can inspect and manipulate attributes. From there, I have the ability to add, remove, and even change an attribute using these methods:</p>
```javascript
// Add a class to all list items that are numbered even.
$('li:even').addClass('even-item');

// Remove all classes from any paragraph.
$('p').removeClass();

// Used to find and set the value of the title attribute of any abbr element.
$('abbr').attr('title', 'Hello World');
```
<p><b>Attribute Manipulation Methods:</b> `.addClass()`, `.attr()`, `.hasClass()`, `.prop()`, `.removeAttr()`, `.removeClass()`, `.removeProp()`, `.toggleClass()`, `.val()`</p>
</details>

<details>
<summary>How can I manipulate styles?</summary>
<p>When reading or setting the height, width, or position of an element, I can use a handful of special methods. For all other style manipulation, I can use the `.css()` method to handle any CSS alterations. The `.css()` method in particular may be used to set one property or many, but the syntax varies. To set a single property, I should use a property name and value in quotation marks, separated by a comma. To set multiple properties, they should be nested within curly braces, with the property name in camelCase, followed by a colon and the quoted value. Other measurement units must be identified followed by the quoted measurement.</p>
```javascript
// Single property
$('h1 span').css('font-size', 'normal');

// Multiple properties
$('div').css({
  fontSize: '13px',
  background: '#f60'
});

$('header').height(200);
$('.extend').height(30 + 'em');
```
<p><b>Style Manipulation Methods:</b> `.css()`, `.height()`, `.innerHeight()`, `.innerWidth()`, `.offset()`, `.outerHeight()`, `.outerWidth()`, `.position()`, `.scrollLeft()`, `.scrollTop()`, `.width()`</p>
</details>

<details>
<summary>How do I manipulate the DOM itself?</summary>
<p>I can also manipulate the Document Object Model (DOM) by changing the placement of elements, adding and removing elements, or just flat-out altering elements. Each individual DOM manipulation method has its own syntax.</p>
<p><b>Examples:</b></p>
```javascript
// Adding a new h3 with the prepend() method inside any section
$('section').prepend('<h3>Featured</h3>');

// Adding a new em element just after the link
$('a[target="_blank"]').after('<em>New window.</em>');

// Replacing the text of any h1 element with "Hello World"
$('h1').text('Hello World');
```
</details>

## Events

<details>
<summary>What's an event handler and how do I add one?</summary>
<p>An event handler is a method that is called only upon a specific event or action taking place. For example, the method of adding a class to an element can be set to only occur when it is clicked upon.</p>
```javascript
$('li').click(function(event){
  $(this).addClass('saved-item');
});
```
<p>Here, I've grabbed all list items. The `.click()` event method is bound to the list item selector, setting up an action for an element to be saved. I'm also using the `.addClass()` method to give it the class of `saved-item`.</p>
<p><b>Events Link:</b> <a href="https://api.jquery.com/category/events/" target="_blank">https://api.jquery.com/category/events/</a></p>
</details>

<details>
<summary>What is the `.on()` method and why is it more flexible?</summary>
<p>From the `.click()` event method, I should consider the `.on()` method. It is more flexible, using delegation for elements that get added to the page dynamically. It uses the native event name, while the function handles the event. It is only called in place of the `.click()` method, which is now passed as the first argument inside the `.on()` method, while the rest stays the same as before.</p>
```javascript
$('li').on('click', function(event){
  $(this).addClass('saved-item');
});
```
</details>

<details>
<summary>Can I nest events?</summary>
<p>Yes, it is possible to have multiple event handlers and triggers nested within one another. I should consider how the `.on()` method can pass the `hover` argument over the class of `pagination`. Upon calling the `.on()` event, the `.click()` event is called on the anchor with the `up` ID.</p>
```javascript
$('.pagination').on('hover', function(event){
  $('a#up').click();
});
```
</details>

<details>
<summary>Show me that Event Demo again.</summary>
<p><b>HTML</b></p>
```html
<div class="notice-warning">
  <div class="notice-close">&#215;</div>
  <strong>Warning!</strong> I&#8217;m about to lose my cool.
</div>
```
<p><b>JavaScript</b></p>
```javascript
$('.notice-close').on('click', function(event){
  $('.notice-warning').remove();
});
```
</details>

## Effects

<details>
<summary>What kind of effects does jQuery offer?</summary>
<p>jQuery offers effects from showing or hiding content, fading in or out, to sliding content up and down. All these methods use customized syntax from the jQuery documentation and accept arguments for duration, easing, and the ability to specify a callback.</p>
<p><b>Effects Link:</b> <a href="https://api.jquery.com/category/effects/" target="_blank">https://api.jquery.com/category/effects/</a></p>
</details>

<details>
<summary>How do I set the duration for an effect?</summary>
<p>Using the `.show()` method as an example, I can set the duration using keywords or a millisecond value. 'slow' defaults to 600 milliseconds and 'fast' to 200 milliseconds.</p>
```javascript
$('.error').show('fast');
$('.error').show('slow');
$('.error').show(500);
```
</details>

<details>
<summary>How do I set the easing for an effect?</summary>
<p>In addition to setting the duration, the easing (or speed at which an animation progresses) may also be set. I can use either of two keywords: <b>swing</b> (starts slow, speeds up, then slows down) or <b>linear</b> (runs at one constant pace). For more easing values, I need to remember I can use a plug-in like jQuery UI.</p>
<p><b>jQuery UI Link:</b> <a href="https://jqueryui.com/" target="_blank">https://jqueryui.com/</a></p>
```javascript
$('.error').show('slow', 'linear');
$('.error').show(500, 'swing');
```
</details>

<details>
<summary>What is an effect callback?</summary>
<p>When an animation is completed, it is possible to run another function, called a callback function. It should be placed after the duration or easing argument, following the syntax:</p>
```javascript
$('.error').show('slow', 'linear', function(event){
  $('.error .status').text('Continue');
});
```
</details>

<details>
<summary>Can I see the example of using a callback with an effect?</summary>
<p><b>HTML</b></p>
```html
<div class="notice-warning">
  <div class="notice-close">&#215;</div>
  <strong>Warning!</strong> I&#8217;m about to lose my cool.
</div>
```
<p><b>JavaScript</b></p>
```javascript
$('.notice-close').on('click', function(event){
  $('.notice-warning').fadeOut('slow', function(event){
    $(this).remove();
  });
});
```
<p>The `.remove()` is used as a callback to the `fadeOut()` method so that the alert disappears and is then removed from the DOM once the fade is complete.</p>
</details>

<details>
<summary>Can I list the main effect methods?</summary>
<ul>
<li><b>Basic Effects:</b> `.hide()`, `.show()`, `.toggle()`</li>
<li><b>Custom Effects:</b> `.animate()`, `.clearQueue()`, `.delay()`, `.dequeue()`, `.queue()`, `.stop()`</li>
<li><b>Fading Effects:</b> `.fadeIn()`, `.fadeOut()`, `.fadeTo()`, `.fadeToggle()`</li>
<li><b>Sliding Effects:</b> `.slideDown()`, `.slideToggle()`, `.slideUp()`</li>
</ul>
</details>

<details>
<summary>Can I review the sliding panel demo?</summary>
<p><b>HTML</b></p>
```html
<div class="panel">
  <div class="panel-stage"></div>
  <a href="#" class="panel-tab">Open <span>&#9660;</span></a>
</div>
```
<p><b>JavaScript</b></p>
```javascript
$('.panel-tab').on('click', function(event){
  event.preventDefault();
  $('.panel-stage').slideToggle('slow', function(event){
    if($(this).is(':visible')){
      $('.panel-tab').html('Close <span>&#9650;</span>');
    } else {
      $('.panel-tab').html('Open <span>&#9660;</span>');
    }
  });
});
```
</details>

<details>
<summary>Can I review the tabs demo?</summary>
<p><b>HTML</b></p>
```html
<ul class="tabs-nav">
  <li><a href="#tab-1">Features</a></li>
  <li><a href="#tab-2">Details</a></li>
</ul>
<div class="tabs-stage">
  <div id="tab-1">...</div>
  <div id="tab-2">...</div>
</div>
```
<p><b>JavaScript</b></p>
```javascript
// Show the first tab by default
$('.tabs-stage div').hide();
$('.tabs-stage div:first').show();
$('.tabs-nav li:first').addClass('tab-active');

// Change tab class and display content
$('.tabs-nav a').on('click', function(event){
  event.preventDefault();
  $('.tabs-nav li').removeClass('tab-active');
  $(this).parent().addClass('tab-active');
  $('.tabs-stage div').hide();
  $($(this).attr('href')).show();
});
```
</details>

## Resources & Links

* <a href="https://jsforcats.com/" target="_blank">JavaScript for Cats</a>
* <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Language_overview" target="_blank">MDN JavaScript Guide</a>

</xaiArtifact>\<p\>Remember: \<code\>\&lt;script src="script.js"\&gt;\&lt;/script\&gt;\</code\>\</p\>
\</details\>
