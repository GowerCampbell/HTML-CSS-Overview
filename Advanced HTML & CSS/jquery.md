

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
  * [**MDN JavaScript Guide**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Language_overview): 
