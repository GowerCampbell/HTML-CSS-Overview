<xaiArtifact artifact_id="ea756fa0-736e-4ebc-9501-76b7094a7912" artifact_version_id="2868b123-d49c-4d5b-b878-8751331917f0" title="javascript_jquery_notes.md" contentType="text/markdown">

# jQuery

<details>
<summary>What was that statistic about how many websites use JavaScript and jQuery?</summary>
<p>92% of websites end up using Javascript, often referred to as JS, and jQuery, the format jQuery is used within 63% of them. It is useful to write JavaScript or jQuery to build my own behaviors/OOP functions/classes.</p>
</details>

## JavaScript Intro

<details>
<summary>What are the different roles of HTML, CSS, and JavaScript that I need to remember?</summary>
<p>Adding that interactivity that I obsess about, this is where HTML provides the structure, CSS provides a page with appearance, while JavaScript provides a page with behavior.</p>
</details>

<details>
<summary>How do I save and include a JavaScript file in my HTML?</summary>
<p>Like CSS, Javascript is saved in an external file `.js` using the `<script>` element. I need to remember to place it before the closing `</body>` tag so that the JavaScript is loaded last.</p>
<p>Remember: `<script src="script.js"></script>`</p>
</details>

## Values & Variables

<details>
<summary>What's the basic idea behind values and variables in JavaScript?</summary>
<p>Values are recognized by Javascript. Variables are used to store & share values. These can be strings, booleans, integers, undefined, and null, including but not limited to functions and objects.</p>
</details>

<details>
<summary>How do I define a variable and what are the naming rules?</summary>
<p>A variable is defined by a `var` keyword, an equals sign `=`, and the value, ending with a semicolon `;`.</p>
<p>Variables must begin with a letter, underscore, or dollar `$` sign. They must not start with numbers or contain a hyphen `#`. I also need to remember that they are case-sensitive.</p>
<p>Python uses snake_case while JavaScript uses camelCase without dashes or underscores as a convention.</p>
<p>**Examples:**</p>
```javascript
var theStarterLeague = 125;
var food_truck = 'Coffee';
var mixtape01 = true;
var vinyl = ['Miles Davis', 'Frank Sinatra', 'Ray Charles'];
```
</details>

## Statements

<details>
<summary>What is a JavaScript program made of?</summary>
<p>JavaScript is just a set of statements, which are executed by the browser in the sequence they are written, acting as commands for different behaviors.</p>
<p>**Examples:**</p>
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

-----

## Values & Variables

\<details\>
\<summary\>What's the basic idea behind values and variables in JavaScript?\</summary\>
\<p\>Values are recognized by Javascript. Variables are used to store & share values. These can be strings, booleans, integers, undefined, and null, including but not limited to functions and objects.\</p\>
\</details\>

\<details\>
\<summary\>How do I define a variable and what are the naming rules?\</summary\>
\<p\>A variable is defined by a \<code\>var\</code\> keyword, an equals sign \<code\>=\</code\>, and the value, ending with a semicolon \<code\>;\</code\>.\</p\>
\<p\>Variables must begin with a letter, underscore, or dollar \<code\>$\</code\> sign. They must not start with numbers or contain a hyphen \<code\>\#\</code\>. I also need to remember that they are case-sensitive.\</p\>
\<p\>Python uses snake\_case while JavaScript uses camelCase without dashes or underscores as a convention.\</p\>
\<p\>\<b\>Examples:\</b\>\</p\>
\<pre\>\<code\>var theStarterLeague = 125;
var food\_truck = 'Coffee';
var mixtape01 = true;
var vinyl = ['Miles Davis', 'Frank Sinatra', 'Ray Charles'];\</code\>\</pre\>
\</details\>

-----

## Statements

\<details\>
\<summary\>What is a JavaScript program made of?\</summary\>
\<p\>JavaScript is just a set of statements, which are executed by the browser in the sequence they are written, acting as commands for different behaviors.\</p\>
\<p\>\<b\>Examples:\</b\>\</p\>
\<pre\>\<code\>log(polaroid);
return('bicycle lane');
alert('Congratulations, you ' + outcome);\</code\>\</pre\>
\</details\>

-----

## Functions

\<details\>
\<summary\>What are functions and how do I define one?\</summary\>
\<p\>Functions perform a set of scripted behaviors. They are saved for later and, depending on the function, they may even accept different arguments.\</p\>
\<p\>A function is defined by using the \<code\>function\</code\> keyword, followed by a name and parentheses \<code\>()\</code\>. The code to be executed is placed within enclosed curly braces \<code\>{}\</code\>.\</p\>
\</details\>

-----

## Arrays

\<details\>
\<summary\>What's an array and why is it useful?\</summary\>
\<p\>An array is a way to store a list of items, or values. Arrays are helpful for many reasons, one being the ability to be traversed with different methods or operators. Depending on the situation, arrays can be used to store and return a variety of different values.\</p\>
\<p\>Arrays are set within square brackets \<code\>[]\</code\> with comma-separated items. The items start at index 0 and increase from there.\</p\>
\</details\>

-----

## Objects

\<details\>
\<summary\>What is a JavaScript object?\</summary\>
\<p\>JavaScript is built on the foundation of objects (which are like a dictionary), a collection of keys and values.\</p\>
\<p\>\<b\>Object Example:\</b\>\</p\>
\<pre\>\<code\>// Object
var school = {
name: 'The Starter League',
location: 'Merchandise Mart',
students: 120,
teachers: ['Jeff', 'Raghu', 'Carolyn', 'Shay']
};\</code\>\</pre\>
\<p\>\<b\>Array for Comparison:\</b\>\</p\>
\<pre\>\<code\>// Array
var school = ['Austin', 'Chicago', 'Portland'];\</code\>\</pre\>
\<p\>I need to remember I can use the browser's console to run JavaScript.\</p\>
\</details\>

-----

# jQuery Intro

\<details\>
\<summary\>What is jQuery?\</summary\>
\<p\>It's an open-source JavaScript library written by John Resig that simplifies the interaction between HTML, CSS, and JavaScript.\</p\>
\<p\>\<b\>Course Link:\</b\> \<a href="[https://code.tutsplus.com/30-days-to-learn-jquery--CRS-41c](https://code.tutsplus.com/30-days-to-learn-jquery--CRS-41c)" target="\_blank"\>30 Days to Learn jQuery\</a\>\</p\>
\</details\>

-----

## Getting Started with jQuery

\<details\>
\<summary\>How do I get started with jQuery on my page?\</summary\>
\<p\>I need to set a \<code\>\&lt;script\&gt;\</code\> element to reference it before closing the \<code\>\&lt;/body\&gt;\</code\> tag. Because jQuery is its own library, it is best to keep it separate from all other JavaScript I'm writing.\</p\>
\</details\>

\<details\>
\<summary\>What should I consider when referencing jQuery (minified vs CDN)?\</summary\>
\<p\>I must consider if I want to use the \<b\>minified\</b\> version or the \<b\>uncompressed\</b\> version. Also, I should consider using a content delivery network (\<b\>CDN\</b\>) such as Google Hosted Libraries, especially for a live production environment. Using the minified version from a CDN reduces loading time and has potential caching benefits.\</p\>
\<p\>\<b\>Google Hosted Libraries:\</b\> \<a href="[https://developers.google.com/speed/libraries](https://developers.google.com/speed/libraries)" target="\_blank"\>[https://developers.google.com/speed/libraries](https://developers.google.com/speed/libraries)\</a\>\</p\>
\<pre\>\<code\>\&lt;script src="//[ajax.googleapis.com/ajax/libs/jquery/1.9.0/jquery.min.js](https://www.google.com/search?q=https://ajax.googleapis.com/ajax/libs/jquery/1.9.0/jquery.min.js)"\&gt;\&lt;/script\&gt;
\&lt;script src="script.js"\&gt;\&lt;/script\&gt;
\</code\>\</pre\>
\<p\>All custom and handwritten JavaScript & jQuery should be written in \<code\>script.js\</code\>, as it is placed after jQuery so it may reference keywords in the jQuery library. Notice there is no \<code\>https:\</code\> within the Google CDN to allow for both http and https connections. Without a web server, \<code\>http:\</code\> will need to be included to locate the file on the system's local drive.\</p\>
\</details\>

-----

## The jQuery Object & Document Ready

\<details\>
\<summary\>How do I call the jQuery library in my JavaScript file?\</summary\>
\<p\>I can use either \<code\>$();\</code\> or \<code\>jQuery();\</code\>. This allows me to set up my files.\</p\>
\</details\>

\<details\>
\<summary\>Why do I need to wait for the DOM to be ready, and how do I do it in jQuery?\</summary\>
\<p\>I'm forced to wait for the Document Object Model (DOM) to finish loading. jQuery has a ready event, \<code\>.ready()\</code\>, which ensures that all of my custom functions using jQuery will not be executed until the page has loaded and the DOM is ready.\</p\>
\<pre\>\<code\>$(document).ready(function(event){
// jQuery code
});\</code\>\</pre\>
\</details\>

-----

## Selectors

\<details\>
\<summary\>How does jQuery select elements, and can I see some examples?\</summary\>
\<p\>Mimicking CSS, jQuery can select multiple elements from HTML. Invoking the jQuery object \<code\>$()\</code\> allows me to contain a selector that will return the DOM node(s) to manipulate, as it falls within the parentheses and quotes \<code\>$('...')\</code\>.\</p\>
\<p\>\<b\>Selector Examples:\</b\>\</p\>
\<ul\>
\<li\>\<code\>$('.feature');\</code\> // Class selector\</li\>
\<li\>\<code\>$('li strong');\</code\> // Descendant selector\</li\>
\<li\>\<code\>$('em, i');\</code\> // Multiple selector\</li\>
\<li\>\<code\>$('a[target="\_blank"]');\</code\> // Attribute selector\</li\>
\<li\>\<code\>$('p:nth-child(2)');\</code\> // Pseudo-class selector\</li\>
\</ul\>
\<p\>\<b\>Selector API Link:\</b\> \<a href="[https://api.jquery.com/category/selectors/](https://api.jquery.com/category/selectors/)" target="\_blank"\>[https://api.jquery.com/category/selectors/](https://api.jquery.com/category/selectors/)\</a\>\</p\>
\</details\>

\<details\>
\<summary\>What does the 'this' keyword do inside a jQuery event?\</summary\>
\<p\>I need to consider how it can work within a function, using it to select the element referenced inside the original selector. When an event is raised, using \<code\>this\</code\> as an operator refers to the specific element that was selected in the current handler.\</p\>
\<pre\>\<code\>$('div').click(function(event){
$(this); // 'this' refers to the specific div that was clicked
});\</code\>\</pre\>
\</details\>

-----

## Traversing

\<details\>
\<summary\>What are jQuery Selection Filters and why might they be slow?\</summary\>
\<p\>These are extensions to CSS3 and provide control over selecting an element and its relatives. For example: \<code\>$('div:has(strong)');\</code\>. Used within the selector, however, they are not native to the DOM and can be a bit slow. I should consider using the \<code\>:filter()\</code\> method instead for traversing.\</p\>
\<p\>\<b\>Filter Link:\</b\> \<a href="[https://api.jquery.com/category/selectors/jquery-selector-extensions/](https://api.jquery.com/category/selectors/jquery-selector-extensions/)" target="\_blank"\>jQuery Selector Extensions\</a\>\</p\>
\</details\>

\<details\>
\<summary\>What is traversing and how do I do it?\</summary\>
\<p\>Sometimes CSS selectors alone do not cut it and I need a little more detailed control. Fortunately, jQuery provides a handful of methods for moving up and down the DOM tree, filtering and selecting elements as necessary.\</p\>
\<p\>To get started with filtering elements inside the DOM, a general selection needs to be made from which I will traverse relatively. This allows me to find all \<code\>div\</code\> elements but then exclude the ones chosen by the \<code\>.not()\</code\> method.\</p\>
\<pre\>\<code\>$('div').not('.type, .collection');\</code\>\</pre\>
\</details\>

\<details\>
\<summary\>How does chaining methods work?\</summary\>
\<p\>By using the dot \<code\>.\</code\> to control which methods are called on a selection. Consider this use: \<code\>$('div').not('.type, .collection').parent();\</code\>. Combined together, this will only select the parent elements of \<code\>div\</code\> elements that do not have a class of 'type' or 'collection'.\</p\>
\</details\>

\<details\>
\<summary\>What are the three categories of traversing methods?\</summary\>
\<p\>The jQuery traversing methods fall into three categories:\</p\>
\<ul\>
\<li\>\<b\>Filtering:\</b\> \<code\>.eq()\</code\>, \<code\>.filter()\</code\>, \<code\>.first()\</code\>, \<code\>.has()\</code\>, \<code\>.is()\</code\>, \<code\>.last()\</code\>, \<code\>.map()\</code\>, \<code\>.not()\</code\>, \<code\>.slice()\</code\>\</li\>
\<li\>\<b\>Miscellaneous Traversing:\</b\> \<code\>.add()\</code\>, \<code\>.andSelf()\</code\>, \<code\>.contents()\</code\>, \<code\>.end()\</code\>\</li\>
\<li\>\<b\>DOM Tree Traversal:\</b\> \<code\>.children()\</code\>, \<code\>.closest()\</code\>, \<code\>.find()\</code\>, \<code\>.next()\</code\>, \<code\>.nextAll()\</code\>, \<code\>.nextUntil()\</code\>, \<code\>.offsetParent()\</code\>, \<code\>.parent()\</code\>, \<code\>.parents()\</code\>, \<code\>.parentsUntil()\</code\>, \<code\>.prev()\</code\>, \<code\>.prevAll()\</code\>, \<code\>.prevUntil()\</code\>, \<code\>.siblings()\</code\>\</li\>
\</ul\>
\<p\>\<b\>Traversing Methods Link:\</b\> \<a href="[https://api.jquery.com/category/traversing/](https://api.jquery.com/category/traversing/)" target="\_blank"\>[https://api.jquery.com/category/traversing/](https://api.jquery.com/category/traversing/)\</a\>\</p\>
\</details\>

-----

## Manipulation

\<details\>
\<summary\>What are the main ways I can manipulate elements with jQuery?\</summary\>
\<p\>After selecting and traversing elements in the DOM, I can use the library to manipulate these elements either by reading, adding, or changing attributes or styles. Additionally, elements can be altered, such as changing their placement, removing them, adding new elements, and so forth.\</p\>
\<p\>\<b\>Manipulation Link:\</b\> \<a href="[https://api.jquery.com/category/manipulation/](https://api.jquery.com/category/manipulation/)" target="\_blank"\>[https://api.jquery.com/category/manipulation/](https://api.jquery.com/category/manipulation/)\</a\>\</p\>
\</details\>

\<details\>
\<summary\>How do I get and set information with jQuery?\</summary\>
\<p\>There are two directives: getting information and setting it. This revolves around using a selector to determine what information is to be retrieved or changed.\</p\>
\<pre\>\<code\>// Gets the value of the alt attribute
$('img').attr('alt');

// Sets the value of the alt attribute
$('img').attr('alt', 'Wild kangaroo');\</code\>\</pre\>

\</details\>

\<details\>
\<summary\>How can I manipulate attributes?\</summary\>
\<p\>I can inspect and manipulate attributes. From there, I have the ability to add, remove, and even change an attribute using these methods:\</p\>
\<pre\>\<code\>// Add a class to all list items that are numbered even.
$('li:even').addClass('even-item');

// Remove all classes from any paragraph.
$('p').removeClass();

// Used to find and set the value of the title attribute of any abbr element.
$('abbr').attr('title', 'Hello World'); \</code\>\</pre\>

\<p\>\<b\>Attribute Manipulation Methods:\</b\> \<code\>.addClass()\</code\>, \<code\>.attr()\</code\>, \<code\>.hasClass()\</code\>, \<code\>.prop()\</code\>, \<code\>.removeAttr()\</code\>, \<code\>.removeClass()\</code\>, \<code\>.removeProp()\</code\>, \<code\>.toggleClass()\</code\>, \<code\>.val()\</code\>\</p\>
\</details\>

\<details\>
\<summary\>How can I manipulate styles?\</summary\>
\<p\>When reading or setting the height, width, or position of an element, I can use a handful of special methods. For all other style manipulation, I can use the \<code\>.css()\</code\> method to handle any CSS alterations. The \<code\>.css()\</code\> method in particular may be used to set one property or many, but the syntax varies. To set a single property, I should use a property name and value in quotation marks, separated by a comma. To set multiple properties, they should be nested within curly braces, with the property name in camelCase, followed by a colon and the quoted value. Other measurement units must be identified followed by the quoted measurement.\</p\>
\<pre\>\<code\>// Single property
$('h1 span').css('font-size', 'normal');

// Multiple properties
$('div').css({
fontSize: '13px',
background: '\#f60'
});

$('header').height(200);
$('.extend').height(30 + 'em');\</code\>\</pre\>

\<p\>\<b\>Style Manipulation Methods:\</b\> \<code\>.css()\</code\>, \<code\>.height()\</code\>, \<code\>.innerHeight()\</code\>, \<code\>.innerWidth()\</code\>, \<code\>.offset()\</code\>, \<code\>.outerHeight()\</code\>, \<code\>.outerWidth()\</code\>, \<code\>.position()\</code\>, \<code\>.scrollLeft()\</code\>, \<code\>.scrollTop()\</code\>, \<code\>.width()\</code\>\</p\>
\</details\>

\<details\>
\<summary\>How do I manipulate the DOM itself?\</summary\>
\<p\>I can also manipulate the Document Object Model (DOM) by changing the placement of elements, adding and removing elements, or just flat-out altering elements. Each individual DOM manipulation method has its own syntax.\</p\>
\<p\>\<b\>Examples:\</b\>\</p\>
\<pre\>\<code\>// Adding a new h3 with the prepend() method inside any section
$('section').prepend('\&lt;h3\&gt;Featured\&lt;/h3\&gt;');

// Adding a new em element just after the link
$('a[target="\_blank"]').after('\<em\>New window.\</em\>');

// Replacing the text of any h1 element with "Hello World"
$('h1').text('Hello World');\</code\>\</pre\>

\</details\>

-----

## Events

\<details\>
\<summary\>What's an event handler and how do I add one?\</summary\>
\<p\>An event handler is a method that is called only upon a specific event or action taking place. For example, the method of adding a class to an element can be set to only occur when it is clicked upon.\</p\>
\<pre\>\<code\>$('li').click(function(event){
$(this).addClass('saved-item');
});\</code\>\</pre\>
\<p\>Here, I've grabbed all list items. The \<code\>.click()\</code\> event method is bound to the list item selector, setting up an action for an element to be saved. I'm also using the \<code\>.addClass()\</code\> method to give it the class of `saved-item`.\</p\>
\<p\>\<b\>Events Link:\</b\> \<a href="[https://api.jquery.com/category/events/](https://api.jquery.com/category/events/)" target="\_blank"\>[https://api.jquery.com/category/events/](https://api.jquery.com/category/events/)\</a\>\</p\>
\</details\>

\<details\>
\<summary\>What is the `.on()` method and why is it more flexible?\</summary\>
\<p\>From the \<code\>.click()\</code\> event method, I should consider the \<code\>.on()\</code\> method. It is more flexible, using delegation for elements that get added to the page dynamically. It uses the native event name, while the function handles the event. It is only called in place of the \<code\>.click()\</code\> method, which is now passed as the first argument inside the \<code\>.on()\</code\> method, while the rest stays the same as before.\</p\>
\<pre\>\<code\>$('li').on('click', function(event){
$(this).addClass('saved-item');
});\</code\>\</pre\>
\</details\>

\<details\>
\<summary\>Can I nest events?\</summary\>
\<p\>Yes, it is possible to have multiple event handlers and triggers nested within one another. I should consider how the \<code\>.on()\</code\> method can pass the `hover` argument over the class of `pagination`. Upon calling the \<code\>.on()\</code\> event, the \<code\>.click()\</code\> event is called on the anchor with the `up` ID.\</p\>
\<pre\>\<code\>$('.pagination').on('hover', function(event){
$('a\#up').click();
});\</code\>\</pre\>
\</details\>

\<details\>
\<summary\>Show me that Event Demo again.\</summary\>
\<p\>\<b\>HTML\</b\>\</p\>
\<pre\>\<code\>\&lt;div class="notice-warning"\&gt;
\&lt;div class="notice-close"\&gt;\&amp;\#215;\&lt;/div\&gt;
\&lt;strong\&gt;Warning\!\&lt;/strong\&gt; I\&amp;\#8217;m about to lose my cool.
\&lt;/div\&gt;\</code\>\</pre\>
\<p\>\<b\>JavaScript\</b\>\</p\>
\<pre\>\<code\>$('.notice-close').on('click', function(event){
$('.notice-warning').remove();
});\</code\>\</pre\>
\</details\>

-----

## Effects

\<details\>
\<summary\>What kind of effects does jQuery offer?\</summary\>
\<p\>jQuery offers effects from showing or hiding content, fading in or out, to sliding content up and down. All these methods use customized syntax from the jQuery documentation and accept arguments for duration, easing, and the ability to specify a callback.\</p\>
\<p\>\<b\>Effects Link:\</b\> \<a href="[https://api.jquery.com/category/effects/](https://api.jquery.com/category/effects/)" target="\_blank"\>[https://api.jquery.com/category/effects/](https://api.jquery.com/category/effects/)\</a\>\</p\>
\</details\>

\<details\>
\<summary\>How do I set the duration for an effect?\</summary\>
\<p\>Using the \<code\>.show()\</code\> method as an example, I can set the duration using keywords or a millisecond value. 'slow' defaults to 600 milliseconds and 'fast' to 200 milliseconds.\</p\>
\<pre\>\<code\>$('.error').show('fast');
$('.error').show('slow');
$('.error').show(500);\</code\>\</pre\>
\</details\>

\<details\>
\<summary\>How do I set the easing for an effect?\</summary\>
\<p\>In addition to setting the duration, the easing (or speed at which an animation progresses) may also be set. I can use either of two keywords: \<b\>swing\</b\> (starts slow, speeds up, then slows down) or \<b\>linear\</b\> (runs at one constant pace). For more easing values, I need to remember I can use a plug-in like jQuery UI.\</p\>
\<p\>\<b\>jQuery UI Link:\</b\> \<a href="[https://jqueryui.com/](https://jqueryui.com/)" target="\_blank"\>[https://jqueryui.com/](https://jqueryui.com/)\</a\>\</p\>
\<pre\>\<code\>$('.error').show('slow', 'linear');
$('.error').show(500, 'swing');\</code\>\</pre\>
\</details\>

\<details\>
\<summary\>What is an effect callback?\</summary\>
\<p\>When an animation is completed, it is possible to run another function, called a callback function. It should be placed after the duration or easing argument, following the syntax:\</p\>
\<pre\>\<code\>$('.error').show('slow', 'linear', function(event){
$('.error .status').text('Continue');
});\</code\>\</pre\>
\</details\>

\<details\>
\<summary\>Can I see the example of using a callback with an effect?\</summary\>
\<p\>\<b\>HTML\</b\>\</p\>
\<pre\>\<code\>\&lt;div class="notice-warning"\&gt;
\&lt;div class="notice-close"\&gt;\&amp;\#215;\&lt;/div\&gt;
\&lt;strong\&gt;Warning\!\&lt;/strong\&gt; I\&amp;\#8217;m about to lose my cool.
\&lt;/div\&gt;\</code\>\</pre\>
\<p\>\<b\>JavaScript\</b\>\</p\>
\<pre\>\<code\>$('.notice-close').on('click', function(event){
$('.notice-warning').fadeOut('slow', function(event){
$(this).remove();
});
});\</code\>\</pre\>
\<p\>The \<code\>.remove()\</code\> is used as a callback to the \<code\>fadeOut()\</code\> method so that the alert disappears and is then removed from the DOM once the fade is complete.\</p\>
\</details\>

\<details\>
\<summary\>Can you list the main effect methods?\</summary\>
\<ul\>
\<li\>\<b\>Basic Effects:\</b\> \<code\>.hide()\</code\>, \<code\>.show()\</code\>, \<code\>.toggle()\</code\>\</li\>
\<li\>\<b\>Custom Effects:\</b\> \<code\>.animate()\</code\>, \<code\>.clearQueue()\</code\>, \<code\>.delay()\</code\>, \<code\>.dequeue()\</code\>, \<code\>.queue()\</code\>, \<code\>.stop()\</code\>\</li\>
\<li\>\<b\>Fading Effects:\</b\> \<code\>.fadeIn()\</code\>, \<code\>.fadeOut()\</code\>, \<code\>.fadeTo()\</code\>, \<code\>.fadeToggle()\</code\>\</li\>
\<li\>\<b\>Sliding Effects:\</b\> \<code\>.slideDown()\</code\>, \<code\>.slideToggle()\</code\>, \<code\>.slideUp()\</code\>\</li\>
\</ul\>
\</details\>

\<details\>
\<summary\>Can I review the sliding panel demo?\</summary\>
\<p\>\<b\>HTML\</b\>\</p\>
\<pre\>\<code\>\&lt;div class="panel"\&gt;
\&lt;div class="panel-stage"\&gt;\&lt;/div\&gt;
\&lt;a href="\#" class="panel-tab"\&gt;Open \&lt;span\&gt;\&amp;\#9660;\&lt;/span\&gt;\&lt;/a\&gt;
\&lt;/div\&gt;\</code\>\</pre\>
\<p\>\<b\>JavaScript\</b\>\</p\>
\<pre\>\<code\>$('.panel-tab').on('click', function(event){
event.preventDefault();
$('.panel-stage').slideToggle('slow', function(event){
if($(this).is(':visible')){
$('.panel-tab').html('Close \&lt;span\&gt;\&amp;\#9650;\&lt;/span\&gt;');
} else {
$('.panel-tab').html('Open \&lt;span\&gt;\&amp;\#9660;\&lt;/span\&gt;');
}
});
});\</code\>\</pre\>
\</details\>

\<details\>
\<summary\>Can I review the tabs demo?\</summary\>
\<p\>\<b\>HTML\</b\>\</p\>
\<pre\>\<code\>\&lt;ul class="tabs-nav"\&gt;
\&lt;li\&gt;\&lt;a href="\#tab-1"\&gt;Features\&lt;/a\&gt;\&lt;/li\&gt;
\&lt;li\&gt;\&lt;a href="\#tab-2"\&gt;Details\&lt;/a\&gt;\&lt;/li\&gt;
\&lt;/ul\&gt;
\&lt;div class="tabs-stage"\&gt;
\&lt;div id="tab-1"\&gt;...\&lt;/div\&gt;
\&lt;div id="tab-2"\&gt;...\&lt;/div\&gt;
\&lt;/div\&gt;\</code\>\</pre\>
\<p\>\<b\>JavaScript\</b\>\</p\>
\<pre\>\<code\>// Show the first tab by default
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
});\</code\>\</pre\>

\</details\>

-----

## Resources & Links

  * \<a href="[https://jsforcats.com/](https://jsforcats.com/)" target="\_blank"\>JavaScript for Cats\</a\>
  * \<a href="[https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Language\_overview](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Language_overview)" target="\_blank"\>MDN JavaScript Guide\</a\>
