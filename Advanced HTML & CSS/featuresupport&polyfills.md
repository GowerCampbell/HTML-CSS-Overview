# Feature Support & Polyfills

Building a website - rewards & fustrations (each browsers changes the look and performance of a website)

Websites do not need to look or perform the same in every browser.

And a browser can drop support for a website if it not getting enough traffic. If traffic is not contributing to thousand of dollars in sales, support may be mandatory.

Best practices for a website to perform adequately in all browsers is to create **fallback in your CSS3**. Other techniques include **shivs** and **polyfills** (JavaScript plugins that support for a requested set of features not natively supported by an specfic browser).

-----

## HTML5 Shiv & Shims

Because new elements cannot hold children and are unaffected by CSS, the **HTML5 Shiv** created by Remy Sharp provides the ability to use HTML5 elements within older versions of vendors. Allowing support to reach HTML5 to be stylised.

  * **Link:** [https://www.paulirish.com/2011/the-history-of-the-html5-shiv/](https://www.paulirish.com/2011/the-history-of-the-html5-shiv/)
  * **Download Link:** [https://github.com/afarkas/html5shiv](https://github.com/afarkas/html5shiv)

(Hosted on your server: use for best performance the javascript file within the head of the document after the styesheets references. Include a conditional comment: [https://css-tricks.com/how-to-create-an-ie-only-stylesheet/](https://css-tricks.com/how-to-create-an-ie-only-stylesheet/))

```html
```

### The Difference Between a Shiv & a Shim

Both HTML5 Shiv and shim are the same and are used interchangeably and commonly transposed.

### Element Display Properties

Additionally, once new HTML5 elements are created like `<permissionn>` using any bloack level need to be identified and updated using the `display: block;` declaration.

Lastly, Browsers do not correctly define styles for a few new HTML5 inline-block level elements. These need to be explicitly stated.

```css
audio,
canvas,
video {
  display: inline-block;
}
```

-----

## Detecting Browser Features with Modernizr

Referencing the HTML5 Shiv with a conditional comment as it helps you traget browsers that are new to HTML5 features & elements.

Use **Feature detection**, provided by **Modernizr**.

  * **Link:** [https://modernizr.com/](https://modernizr.com/)

A way to write CSS & JavaScript bsed on whether a browsers supports a specific feature. Modernizr will add the class of `borderradius` to the `<html>` element. If the browser doesnt support it will aadd the class of `no-borderradius` to the html element.

### Loading Modernizr

  * **Download Link:** [https://modernizr.com/download/?setclasses](https://modernizr.com/download/?setclasses)

Once downloded, upload the JavaScript file on your server and reference.

```html
<script src="modernizr.js"></script>
```

*Configged to HTML5 Shiv*

-----

## Conditional Logic with Modernizr

### Conditionally Applying CSS Styles

Once modernizr is running CSS styles my be conditionlly applied based on the features a browser supports. All will detect for the mjority of the CSS3 properties and values in the documentation: [https://modernizr.com/docs/](https://modernizr.com/docs/)

Know that fallbacks can still be used to support RGBa with hexadeciml, keep your styles organized and performnce in mind.

```css
/* Base Button Styles */
button {
  border: 0;
  color: #fff;
  cursor: pointer;
  font-size: 14px;
  font-weight: 600;
  margin: 0;
  outline: 0;
}

/* With CSS Gradient Styles */
.cssgradients button {
  border: 1px solid #0080c2;
  background: linear-gradient(#00a2f5, #0087cc);
  border-radius: 6px;
  padding: 15px 30px;
}
.cssgradients button:hover {
  background: linear-gradient(#1ab1ff, #009beb);
}
.cssgradients button:active {
  box-shadow: inset 0 1px 10px rgba(255, 255, 255, .5);
}

/* Without CSS Gradient Styles */
.no-cssgradients button {
  background: transparent url("button.png") 0 0 no-repeat;
  padding: 16px 31px;
}
.no-cssgradients button:hover {
  background-position: 0 -49px;
}
.no-cssgradients button:active {
  background-position: 0 -98px;
}
```

In the demonstrtion, the button inherits default styles, however, specfic styles wil apply based on whether CSS3 gradient bckground is supported.

With this code none of he styles: background, rounded corners and a box shadow are over written and an HTTP request is only made when necessry.

When working CSS3 feature detection, it is hard to know what styles will look in browsers that do not support a specfic CSS3 features. Use bookmarklet: [https://github.com/davatron5000/deCSS3](https://github.com/davatron5000/deCSS3) to disable any CSS3 fetures, sdoing so allows you to see what a website would look like without CSS3 and if your conditional styles are working.

### Conditionally Loading Files

  * **Link:** [https://modernizr.com/docs/\#using-modernizr-with-javascript](https://modernizr.com/docs/#using-modernizr-with-javascript)

Using Modernizr with JavaScript to expose additional features.

With this, JavaScript **polyfills** (is a piece of code that enables modern HTML, CSS, or JavaScript features in older browsers that do not support them natively.) And Conditional files can be loaded based on the detection of a given feature with the help of jQuery `getScript` method.

```javascript
$(document).ready(function() {
  if (Modernizr.localstorage) {
    // Local storage is available
    jQuery.getScript('storage.js');
  } else {
    // Local storage is not available
    jQuery.getScript('storage-polyfill.js');
  }
});
```

Most of all use Modernizr to set the condition of an `if` statement in JavaScript for different scipts using `localstorage` the `storage.js` to load them or if the local storage is not supported, jQuery uses `storage-polyfill.js` using the `getScript()`.

### Conditionally Loading based on Media Queries

You can use Mordernizr to test agaisnt media quries, doing so provides the ability to only load files based on different media query conditions. Not loading unnecessary files to be beneficial for performance.

```javascript
$(document).ready(function() {
  if (Modernizr.mq('screen and (min-width: 640px)')) {
    jQuery.getScript('tabs.js');
  }
});
```

Above, detecting screens above 640 pixels wide, primarily desktops, it loads the `tabs.js` based off of this. This condition is tested once when the page loads. And will not be retested if the user resizes the page.

### Conditionally Running Scripts

Modernizr, all HTML5 & CSS3 features they detect may be tested with JavaScript, for example disabling tooltips on modile due to not having hover capabilitys and instead show it in plain text.

```javascript
$(document).ready(function() {
  if (Modernizr.mq('screen and (max-width: 400px)')) {
    $('.size').text('small');
  }
});
```

Above is basic javScript which executed whether upon loading the screen is above 400px it will swap text.

-----

## HTML5 & CSS3 Polyfills

List of Polyfills to be dropped in when needed.

  * **Link:** [https://github.com/Modernizr/Modernizr/wiki/HTML5-Cross-browser-Polyfills](https://github.com/Modernizr/Modernizr/wiki/HTML5-Cross-browser-Polyfills)

Including a list of all the new HTML5 & CSS3 Features for a fallback or used outright:

  * **Link:** [https://html5please.com/](https://html5please.com/)

-----

## Cross Browser Testing

The most dreaded part of web design and development is cross browser testng, making sure website works well in all browsers: chrome, firefox, and safari. We can use test softwares from these services to create virtual machnes:

  * **Link:** [https://www.smashingmagazine.com/2011/08/a-dozen-cross-browser-testing-tools/](https://www.smashingmagazine.com/2011/08/a-dozen-cross-browser-testing-tools/)

Microsoft provides a handful of virtualPCs for testing, which set up is too complicated.

Greg Thornton build an automated installer:

  * **Link:** [https://github.com/xdissent/ievms](https://github.com/xdissent/ievms)

Only instll the necessary virtual mchines and clear up disk soace ahead of time. Consider set up on an external harddrive.

Internet Explorer has built-in development tools like web inspector and debugging tools we love.

-----

<details>
<summary>Test Yourself</summary>

  <details>
  <summary>What problem does the HTML5 Shiv solve?</summary>
  It allows older browsers (like IE < 9) to recognize and style new HTML5 elements (e.g., `<section>`, `<article>`), which they would otherwise treat as unknown inline elements.
  </details>

  <details>
  <summary>What is the difference between a "shiv" and a "shim"?</summary>
  According to these notes, they are the same, and the terms are used interchangeably.
  </details>

  <details>
  <summary>How does Modernizr help with applying conditional CSS?</summary>
  It detects if a browser supports a specific feature (like CSS gradients) and adds a class to the `<html>` tag (e.g., `.cssgradients` or `.no-cssgradients`). You can then target these classes in your CSS to provide styles for browsers that do or do not support the feature.
  </details>

  <details>
  <summary>What is a polyfill?</summary>
  It's a piece of code (usually JavaScript) that provides the functionality of a modern web feature in older browsers that don't natively support it.
  </details>

  <details>
  <summary>Why is it beneficial to conditionally load a script based on a media query?</summary>
  It improves performance by not loading unnecessary files. For example, you can avoid loading a complex JavaScript file for desktop-only features on a mobile device.
  </details>

</details>
