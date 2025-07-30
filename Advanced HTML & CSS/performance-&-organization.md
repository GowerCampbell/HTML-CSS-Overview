

# Performance & Organization

How do we design the right structure for a code base and identify all the different components that work together, how do we speed up production and make a better experience?

## Strategy & Structure
Where developing the code base, building a strong directory architecture, outlining design patterns and how to find ways to reuse common code?

### Style Architecture
What type of styles can we create based on intent, which include creating directories for a common base styles, user interface components and business logic modules?

**Base (Common styles & variables used across the entire website)**  
- normalize.css  
- layout.css  
- typography.css  

**Components (User Interface Elements)**  
- alerts.css  
- buttons.css  
- forms.css  
- nav.css  
- tables.css  

**Modules (Business Needs)**  
- aside.css  
- footer.css  
- header.css  

Why do we start thinking of websites as systems rather than individual pages?  
- Viewing websites as systems encourages a modular, reusable approach, where components and styles are designed to work cohesively across the entire site, improving maintainability and scalability.

How is it important that the modules contain styles that are specific to business logic?  
- Modules tailored to business logic ensure that styles are purpose-driven, aligning with specific functionality or branding requirements, which enhances clarity and reduces unnecessary style conflicts.

When using different components to mark up HTML, how does the separation of style encourage well-thought-out presets and the ability for styles to be widely shared and reused?  
- Separating styles into distinct categories (base, components, modules) promotes modularity, making it easier to reuse styles across different parts of the site while maintaining consistency and reducing redundancy.

Researching CSS methodologies such as Object-Oriented CSS (OOCSS) or Scalable and Modular Architecture for CSS (SMACSS):  
- These methodologies provide structured approaches to organizing CSS, focusing on reusability, scalability, and maintainability.

## Object-Oriented CSS (OOCSS)
Created by Nicole Sullivan  
Link: https://oocss.org/about-us (CSS Code Wars)  
- Separate structure from skin  
- Separate content from container  

By allowing styles to be inherited and displayed without conflict, how do we go about abstracting the layout of an element from the theme of a website?  
- In using a solid grid and layout structure, along with well-crafted modules, we create a foundation where layout (structure) is independent of visual design (skin), enabling flexible theming without altering the core layout.

By separating content from the container, do we remove the dependency of a parent element by nesting children?  
- Elements need to inherit default styles that can be extended with multiple classes, reducing reliance on nested hierarchies and promoting flexibility.

**HTML Example**  
```html
<div class="alert alert-error">
  <p class="msg">...</p>
</div>
```

**CSS Example**  
```css
.alert {...}
.alert-error {...}
.msg {...}
```

Remember: Object-Oriented CSS advocates building a component library, staying flexible, and utilizing a grid?

## Scalable & Modular Architecture for CSS (SMACSS)
Developed by Jonathan Snook  
Link: https://smacss.com/  
Breaking up styles into five core categories:  
- **Base**: Core elements, general defaults (e.g., resets, typography)  
- **Layout**: Sizing and grid styles for different elements  
- **Module**: Targeted elements like navigation or feature styles  
- **State**: Augments or overrides other styles (e.g., active tab states)  
- **Theme**: Styles based on the skin, look, and feel  

**HTML Example**  
```html
<div class="alert is-error">
  <p>...</p>
</div>
```

**CSS Example**  
```css
.alert {...}
.alert.is-error {...}
.alert p {...}
.alert.is-error p {...}
```

Remember: The `alert` class falls into the module category, while `is-error` falls into the state category; both inherit from layout, base, and theme categories.

## Choosing a Methodology
CSS grows with site size; more code leads to more problems.  
How do we ensure loose coupling (interdependence between CSS elements)?  
- Maintain loose coupling by minimizing dependencies between styles, allowing components to function independently.

How do we maintain, review, and refactor CSS to avoid overriding main styles?  
- Regularly review CSS for redundancy, ensure readability of markup, and avoid excessive nesting to improve cohesion (the degree to which all elements work toward a single task).

Consider the readability of markups (tags that define elements). Do not just nest dependencies; consider your code’s cohesion.  
Link: https://www.viget.com/articles/css-squareoff/

## Performance-Driven Selectors
How do styles applied to correct elements ensure the page renders performantly, avoiding non-performant @decorators?  
From basic selectors: type (`<div>`), ID (`#header`), or class (`.tweet`)  
Pseudo-classes (`:hover`) or regex selectors (`:first-child`, `[class^="grid-"]`)  

**Combining Selectors**  
Using both a `#nav` with `<a>` element, where browsers read selectors right-to-left to match with the same set of elements, consider the Document Object Model (DOM) such as nodes and objects that interact with a page.

**The Key Selector**  
```css
#content .intro {}
```
A performant selector that matches the element with the properties, e.g., `#social a {}` to target a specific class.

**Overqualifying Selectors**  
For example, `#content a {}` forces the browser to look through everything, while `#nav li a {}` vs. `#nav a {}` depends on the site. How do we achieve better CSS parsing speeds when browsers do all the work?  
- Use minimal, specific selectors to reduce parsing time.

Link: http://csswizardry.com/2011/09/writing-efficient-css-selectors/

**KEEP SELECTORS SHORT**  
When selectors are short, do they allow better inheritance, portability, and improved efficiency?  
- Short selectors reduce specificity conflicts, improve maintainability, and enhance performance.

```css
/* Bad */
header nav ul li a {...}

/* Good */
.primary-link {...}

/* Bad */
button strong span {...}
button strong span .callout {...}

/* Good */
button span {...}
button .callout {...}
```

Be specific, use classes, and identify parent elements.  
Remember: Don’t be overly specific to avoid breaking the order of elements when they change. Keep selectors with consistent specificity to allow better cooperation.

## Favor Classes
What are the common practices when using classes?  
- Classes are used to build websites’ key selectors, targeting the rightmost element in the selector chain, as it identifies the first element a browser finds in the stack.

Why should we avoid prefixing a class selector with an element?  
- Prefixing prohibits styles from being applied to different elements, increasing specificity unnecessarily.

```css
/* Bad */
#container header nav {...}

/* Good */
.primary-nav {...}

/* Bad */
article.feat-post {...}

/* Good */
.feat-post {...}
```

ID selectors are overly specific and allow for no repetition.

## Why Do We Use Reusable Code?
Bloated file sizes and unnecessary rendering slow down performance. Why should repeating styles or interfaces be combined?  
- Combining styles into a single class allows code to be shared, reducing redundancy and improving maintainability without compromising semantics.

How does pairing selectors together allow styles to be inherited within OOCSS and SMACSS?  
- Pairing selectors enables shared styles, promoting modularity and reusability.

```css
/* Bad */
.news {
  background: #eee;
  border-radius: 5px;
  box-shadow: inset 0 1px 2px rgba(0, 0, 0, .25);
}
.social {
  background: #eee;
  border-radius: 5px;
  box-shadow: inset 0 1px 2px rgba(0, 0, 0, .25);
}

/* Good */
.news,
.social {
  background: #eee;
  border-radius: 5px;
  box-shadow: inset 0 1px 2px rgba(0, 0, 0, .25);
}

/* Even Better */
.modal {
  background: #eee;
  border-radius: 5px;
  box-shadow: inset 0 1px 2px rgba(0, 0, 0, .25);
}
```

## Minify & Compress Files
Why do we remove duplicate and unnecessary code?  
- **Important**: Sending as few bytes of CSS, JS, and HTML markup as possible reduces load times and improves performance.

Use: https://yslow.org/  
To grade your webpage on predefined rules:  
- Example: “This page has 33 external JavaScript scripts. Try combining them into one.”  
- Example: “This page has 5 external stylesheets. Try combining them into one.”  
Includes:  
- Suggestions  
- Page components  
- Statistics  
- Performance  

**CSS Example (Unminified vs. Minified)**  
```css
/* Unminified */
body {
    line-height: 1;
}
ol, ul {
    list-style: none;
}
blockquote, q {
    quotes: none;
}

/* Minified */
body{line-height:1}ol,ul{list-style:none}blockquote,q{quotes:none}
```

How do we ensure compatibility when minifying CSS and JS?  
- Check JavaScript compressors to ensure compatibility (avoid breaking CSS or workflows). Consider using template languages.

How can we create a batch file to combine JS files?  
- Create a batch file to combine multiple JS files (e.g., from a blog’s header or footer) into a single `header.js` or `footer.js` to support all pages.

**Image Optimization**  
Use optimized images to reduce file sizes while maintaining quality:  
- Tool: https://pnggauntlet.com/ (converts files to PNG, supports batch processing)  
- Alternative: VS Code’s Mad’s Beta Image Optimizer Extension  

How do we let the browser cache everything?  
- Use IIS7 in `web.config` to control caching for a componentized, extensible ASP.NET web server:  
```xml
<staticContent>
 <clientCache httpExpires="Sun, 29 Mar 2020 00:00:00 GMT" cacheControlMode="UseExpires" />
</staticContent>
```

**REMEMBER TO COMPRESS EVERYTHING**  
- Remove old third-party libraries.  
- Enable HTTP compression.  
- Minify JS and CSS.  
- Combine CSS and JS files.  
- Use Gzip compression.  
- Set headers and footers.  
- Batch PNGs and JPEGs.  
- Use CSS sprites for tiny images.  
Link: https://www.hanselman.com/blog/nuget-package-of-the-week-1-aspnet-sprite-and-image-optimization

## Gzip Compression
Why do we compress string data types?  
- Compression reduces file sizes sent from server to browser, improving load times.

How do we integrate HTML5 Boilerplate for compression?  
- Add HTML5 Boilerplate to workflows for fast, robust, and adaptable web apps.  
Link: https://github.com/h5bp/html5-boilerplate#quick-start  

Where do we store compression code in HTML5 Boilerplate?  
- Store in the `.htaccess` file in the root directory (Apache web server only). Requires the following modules:  
  - `mod_setenvif.c`  
  - `mod_headers.c`  
  - `mod_deflate.c`  
  - `mod_filter.c`  
  - `mod_expires.c`  
  - `mod_rewrite.c`  

## Measuring Compression
How do we measure compression effectiveness?  
- Use the web inspector (`Ctrl + Shift + I`) to view the network tab, displaying file size and load time. Check how data is encoded with Gzip and deflated.

## Image Compression
What tools do we use for image compression?  
- PC: https://pnggauntlet.com/  
- Mac: https://imageoptim.com/api  

Why does setting image dimensions help rendering speed?  
- Specifying dimensions prevents layout shifts, improving rendering performance.  

```html
<img src="ocean.jpg" height="440" width="660" alt="Oceanview">
```

## How Do We Reduce HTTP Requests to Decrease Load Time?
- Combine like files and use techniques like CSS sprites and Data URIs.

## Combine Like Files
Why does using one CSS and one JavaScript file reduce HTTP load time?  
- Fewer files mean fewer HTTP requests, speeding up page load.

```html
<!-- Bad -->
<link href="css/reset.css" rel="stylesheet">
<link href="css/base.css" rel="stylesheet">
<link href="css/site.css" rel="stylesheet">

<!-- Good -->
<link href="css/styles.css" rel="stylesheet">
```

Why load CSS before JavaScript?  
- CSS should be loaded first to style the page, while JavaScript loads after rendering to avoid blocking the DOM.

## Image Sprites
How do image sprites reduce HTTP requests?  
- Using one background image across multiple elements reduces the number of image requests.

**HTML Example**  
```html
<ul>
  <li><a href="#"><span class="bold">Bold Text</span></a></li>
  <li><a href="#"><span class="italic">Italicize Text</span></a></li>
  <li><a href="#"><span class="underline">Underline Text</span></a></li>
  <li><a href="#"><span class="size">Size Text</span></a></li>
  <li><a href="#"><span class="bullet">Bullet Text</span></a></li>
  <li><a href="#"><span class="number">Number Text</span></a></li>
  <li><a href="#"><span class="quote">Quote Text</span></a></li>
  <li><a href="#"><span class="left">Left Align Text</span></a></li>
  <li><a href="#"><span class="center">Center Align Text</span></a></li>
  <li><a href="#"><span class="right">Right Align Text</span></a></li>
</ul>
```

**CSS Example**  
```css
ul {
  margin: 0;
  padding: 0;
}
li {
  float: left;
  list-style: none;
  margin: 2px;
}
li a {
  background: linear-gradient(#fff, #eee);
  border: 1px solid #ccc;
  border-radius: 3px;
  display: block;
  padding: 3px;
}
li a:hover {
  border-color: #999;
}
li span {
  background: url("https://s3-us-west-2.amazonaws.com/s.cdpn.io/29841/sprite.png") 0 0 no-repeat;
  color: transparent;
  display: block;
  font: 0/0 a;
  height: 16px;
  width: 16px;
}
.italic {
  background-position: -16px 0;
}
.underline {
  background-position: -32px 0;
}
.size {
  background-position: -48px 0;
}
.bullet {
  background-position: -64px 0;
}
.number {
  background-position: -80px 0;
}
.quote {
  background-position: -96px 0;
}
.left {
  background-position: -112px 0;
}
.center {
  background-position: -128px 0;
}
.right {
  background-position: -144px 0;
}
```

## Image Data URI
How do Data URIs reduce HTTP requests?  
- Encoding images within HTML/CSS eliminates separate image requests, ideal for small, static images.

**CSS Example**  
```css
li {
  background:
    url(data:image/gif;base64,R0lGODlhEAAQAMQAAORHHOVSKudfOulrSOp3WOyDZu6QdvCchPGolfO0o/XBs/fNwfjZ0frl3/zy7////wAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAACH5BAkAABAALAAAAAAQABAAAAVVICSOZGlCQAosJ6mu7fiyZeKqNKToQGDsM8hBADgUXoGAiqhSvp5QAnQKGIgUhwFUYLCVDFCrKUE1lBavAViFIDlTImbKC5Gm2hB0SlBCBMQiB0UjIQA7)
    no-repeat
    left center;
  padding: 5px 0 5px 25px;
}
```

**HTML Example**  
```html
<img src="data:image/gif;base64,R0lGODlhEAAQAMQAAORHHOVSKudfOulrSOp3WOyDZu6QdvCchPGolfO0o/XBs/fNwfjZ0frl3/zy7////wAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAACH5BAkAABAALAAAAAAQABAAAAVVICSOZGlCQAosJ6mu7fiyZeKqNKToQGDsM8hBADgUXoGAiqhSvp5QAnQKGIgUhwFUYLCVDFCrKUE1lBavAViFIDlTImbKC5Gm2hB0SlBCBMQiB0UjIQA7" alt="star" width="16" height="16">
```

What is the format of a Data URI?  
- `data:[<mime type>][;charset=<charset>][;base64],<encoded data>`

Converter: https://websemantics.uk/tools/image-to-data-uri-converter/  
Why use Data URIs?  
- Embedding images into base64 Data URIs in HTML or CSS allows caching but is hard to maintain and incompatible with older browsers. The maximum Data URI size is approximately 32,768 bytes.

How can we generate Data URIs in PHP?  
```php
<?php echo base64_encode(file_get_contents("../images/folder16.gif")) ?>
```

When should we use Data URIs?  
- Only use on heavily cached documents. Data URIs can represent any data, including patterns (e.g., http://www.patternify.com/).

**Pattern Example**  
```html
<img height="100" width="660" alt="Rigged Pattern" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAoAAAAICAYAAADA+m62AAAAPUlEQVQYV2NkQAO6m73+X/bdxogujiIAU4RNMVwhuiQ6H6wQl3XI4oy4FMHcCJPHcDS6J2A2EqUQpJhohQAyIyYy0nBAGgAAAABJRU5ErkJggg==">
```

```css
div {
  background: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAoAAAAICAYAAADA+m62AAAAPUlEQVQYV2NkQAO6m73+X/bdxogujiIAU4RNMVwhuiQ6H6wQl3XI4oy4FMHcCJPHcDS6J2A2EqUQpJhohQAyIyYy0nBAGgAAAABJRU5ErkJggg==") repeat;
}
```

## Cache Common Files
How do we avoid reloading common files?  
- Use caching to store images, videos, web fonts, CSS, and JS, reducing repeated requests.

How do we set cache controls with HTML5 Boilerplate?  
- Cache images, videos, and web fonts for a month; cache CSS and JS for a year.  
```apache
ExpiresByType text/css "access plus 1 year"
ExpiresByType application/javascript "access plus 1 year"
```

Link: https://httpd.apache.org/docs/current/mod/mod_expires.html  

## Resources & Links
- https://developer.yahoo.com/performance/rules.html  
- https://www.viget.com/articles/css-squareoff/  
- https://www.hanselman.com/blog/the-importance-and-ease-of-minifying-your-css-and-javascript-and-optimizing-pngs-for-your-blog-or-website  
- https://css-tricks.com/data-uris/  
- https://www.stevesouders.com/blog/2012/02/10/the-performance-golden-rule/  
- https://csswizardry.com/2011/09/writing-efficient-css-selectors/  
- https://html5boilerplate.com/

