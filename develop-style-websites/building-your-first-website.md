
# What was before the internet?
Before the internet, information was primarily accessed through physical media like books, newspapers, magazines, and libraries. Knowledge was also shared via television, radio, and in-person communication, such as lectures or conversations.

# How did we find knowledge?
Knowledge was found through:
- **Libraries**: Using card catalogs and Dewey Decimal systems to locate books and journals.
- **Encyclopedias**: Multi-volume sets like Britannica were key sources for general knowledge.
- **Experts and Institutions**: Consulting professionals, attending classes, or visiting museums.
- **Print Media**: Newspapers, magazines, and academic journals provided up-to-date information.
- **Word of Mouth**: Knowledge was often shared through discussions or storytelling.

# When did the web become the central source of information?
The web became a central source of information in the late 1990s to early 2000s. Key milestones include:
- **Mid-1990s**: The release of browsers like Netscape Navigator and Internet Explorer made the web accessible to the public.
- **Early 2000s**: Search engines like Google improved information retrieval, making the web a go-to resource.
- **Mid-2000s**: The rise of Web 2.0, with user-generated content (e.g., Wikipedia, blogs), solidified the web’s dominance.

# Why are websites built with HTML and CSS, the two most dominant computer languages?
HTML and CSS are foundational for web development because:
- **HTML (HyperText Markup Language)**: Provides structure and meaning to content, defining elements like headings, paragraphs, and links, making it essential for creating web pages.
- **CSS (Cascading Style Sheets)**: Controls the visual presentation, allowing developers to style layouts, colors, and fonts, ensuring websites are visually appealing and user-friendly.
- They are standardized, widely supported by browsers, and relatively simple to learn, making them the backbone of web design.

# What are HTML & CSS?

- **HTML (HyperText Markup Language)**: Used to give structure and meaning to web content, organizing it into elements like headings, paragraphs, and links.
- **CSS (Cascading Style Sheets)**: Used to style the appearance of content, controlling aspects like colors, fonts, layouts, and spacing.

# Understanding Common HTML Terms

- **Elements**: Designators used to define content structure, such as headings (`<h1>` to `<h6>`), paragraphs (`<p>`), links (`<a>`), divisions (`<div>`), inline containers (`<span>`), bold text (`<strong>`), and emphasized text (`<em>`), among others.
- **Tags**: Envelop content within elements using opening (e.g., `<div>`) and closing (e.g., `</div>`) tags. For example: `<a>...</a>`.
- **Attributes**: Properties of an element that provide additional information, e.g., `<a href="http://shayhowe.com/">Learning from Shay Howe</a>`, where `href` is the attribute.

# Setting Up the HTML Document Structure

HTML documents are edited using tools like Visual Studio Code or Sublime Text. A basic HTML structure includes:

- `<!DOCTYPE html>`: Declares the document type as HTML5.
- `<html>`: The root element, with a language attribute (e.g., `lang="en"`).
- `<head>`: Contains metadata, such as character encoding (`<meta charset="utf-8">`) and the page title (`<title>`).
- `<body>`: Holds the visible content of the web page.

Example:
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>Hello World</title>
  </head>
  <body>
    <h1>Hello World</h1>
    <p>This is a web page.</p>
  </body>
</html>
```

# Self-Closing Elements

Also known as void elements, these do not require closing tags. For example, `<meta>` encodes character information. Other common self-closing elements include:
- `<br>`, `<embed>`, `<img>`, `<meta>`, `<wbr>`, `<input>`, `<param>`, `<hr>`, `<link>`, `<source>`

# Code Validation

Ensuring code follows proper linting standards is crucial for correctness and compatibility. Example of a valid HTML structure:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>Styles Conference</title>
  </head>
  <body>
    <h1>Styles Conference</h1>
    <p>Every year the brightest web designers and front-end developers descend on Chicago to discuss the latest technologies. Join us this August!</p>
  </body>
</html>
```

# Understanding Common CSS Terms

- **Selectors**: Designate HTML elements to target and apply styles, e.g., `p {...}` targets all `<p>` elements.
- **Properties**: Determine the style to be applied, such as `background`, `color`, `font-size`, `height`, or `width`.
- **Values**: Define the behavior of the property, e.g., `color: orange;` or `font-size: 16px;`.

Example:
```css
p {
  color: orange;
  font-size: 16px;
}
```

# Working with Selectors

- **Type Selectors**: Target elements by their element type, e.g., `div {...}` applies styles to all `<div>` elements.
  ```css
  div {...}
  ```
  ```html
  <div>...</div>
  <div>...</div>
  ```

- **Class Selectors**: Target elements based on their `class` attribute value, e.g., `.awesome {...}`.
  ```css
  .awesome {...}
  ```
  ```html
  <div class="awesome">...</div>
  <p class="awesome">...</p>
  ```

- **ID Selectors**: Target a single unique element using its `id` attribute, e.g., `#shayhowe {...}`.
  ```css
  #shayhowe {...}
  ```
  ```html
  <div id="shayhowe">...</div>
  ```

- **Additional Selectors**: Learn more at [Shay Howe’s Advanced Selectors](https://learn.shayhowe.com/advanced-html-css/complex-selectors/).

# Referencing CSS

CSS can be applied using:
- **External Style Sheet**: A separate `.css` file linked to the HTML using `<link>`, applying styles across the website.
  ```html
  <head>
    <link rel="stylesheet" href="main.css">
  </head>
  ```
- **Internal CSS**: Defined within a `<style>` tag in the HTML `<head>`.
- **Inline CSS**: Applied directly to elements using the `style` attribute.

# Using CSS Resets

CSS resets apply predefined styles to common HTML elements to ensure consistent rendering across browsers (e.g., for sizing, margins, padding). Examples include:
- [Meyer’s CSS Reset](http://meyerweb.com/eric/tools/css/reset/)
- [Normalize.css](http://necolas.github.io/normalize.css/)

Browsers render elements differently, so cross-browser compatibility and testing are critical.

# In Practice

Example of a CSS reset (Meyer’s Reset v2.0):
```css
/* http://meyerweb.com/eric/tools/css/reset/ 2. v2.0 | 20110126
  License: none (public domain)
*/

html, body, div, span, applet, object, iframe,
h1, h2, h3, h4, h5, h6, p, blockquote, pre,
a, abbr, acronym, address, big, cite, code,
del, dfn, em, img, ins, kbd, q, s, samp,
small, strike, strong, sub, sup, tt, var,
b, u, i, center,
dl, dt, dd, ol, ul, li,
fieldset, form, label, legend,
table, caption, tbody, tfoot, thead, tr, th, td,
article, aside, canvas, details, embed,
figure, figcaption, footer, header, hgroup,
menu, nav, output, ruby, section, summary,
time, mark, audio, video {
  margin: 0;
  padding: 0;
  border: 0;
  font-size: 100%;
  font: inherit;
  vertical-align: baseline;
}
/* HTML5 display-role reset for older browsers */
article, aside, details, figcaption, figure,
footer, header, hgroup, menu, nav, section {
  display: block;
}
body {
  line-height: 1;
}
ol, ul {
  list-style: none;
}
blockquote, q {
  quotes: none;
}
blockquote:before, blockquote:after,
q:before, q:after {
  content: '';
  content: none;
}
table {
  border-collapse: collapse;
  border-spacing: 0;
}
```

Example HTML using an external stylesheet:
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>Styles Conference</title>
    <link rel="stylesheet" href="./assets/stylesheets/main.css">
  </head>
  <body>
    <h1>Styles Conference</h1>
    <p>Every year the brightest web designers and front-end developers descend on Chicago to discuss the latest technologies. Join us this August!</p>
  </body>
</html>
```







