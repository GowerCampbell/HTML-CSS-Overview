
# Getting to Know HTML

## How to Use HTML Elements to Display Types of Content
HTML elements are used to structure and display content on a webpage, with each element serving a specific purpose to ensure content is visually and semantically meaningful. Choosing the right element enhances accessibility, SEO, and user experience.

## Semantics Code Overview
Semantic HTML describes the value and meaning of content on a page, regardless of its style or appearance. It helps browsers, screen readers, and search engines understand the content’s purpose.

## Identifying Divisions `<div>`s & Spans `<span>`s
- **Divisions (`<div>`)**: Act as containers for grouping content, primarily for styling purposes. They are non-semantic and block-level.
- **Spans (`<span>`)**: Inline containers used for styling smaller portions of content, also non-semantic.
- **Paragraphs (`<p>`)**: Semantic block-level elements used for textual content.

Example:
```html
<!-- Division -->
<div class="social">
  <p>I may be found on...</p>
  <p>Additionally, I have a profile on...</p>
</div>

<!-- Span -->
<p>Soon we'll be <span class="tooltip">writing HTML</span> with the best of them.</p>
```

**Note**: `<!-- -->` denotes comments in HTML, ignored by browsers.

## Block vs. Inline Elements
- **Block-Level Elements**:
  - Begin on a new line, stacking vertically.
  - Occupy the full available width.
  - Can contain other block-level or inline elements.
  - Examples: `<div>`, `<p>`, `<h1>`–`<h6>`, `<section>`.
- **Inline-Level Elements**:
  - Do not start on a new line; they flow within the content.
  - Maintain the width of their content.
  - Examples: `<span>`, `<a>`, `<strong>`, `<em>`.

## Using Text-Based Elements

### Headings
Block-level elements used for hierarchical content organization.
```html
<h1>Heading Level 1</h1>
<h2>Heading Level 2</h2>
<h3>Heading Level 3</h3>
<h4>Heading Level 4</h4>
<h5>Heading Level 5</h5>
<h6>Heading Level 6</h6>
```

### Paragraphs
Block-level elements for textual content.
```html
<p>Steve Jobs was a co-founder and longtime chief executive officer at Apple. On June 12, 2005, Steve gave the commencement address at Stanford University.</p>
<p>In his address Steve urged graduates to follow their dreams and, despite any setbacks, to never give up–advice which he sincerely took to heart.</p>
```

### Bold Text with Strong
Semantic inline element indicating strong importance.
```html
<!-- Strong importance -->
<p><strong>Caution:</strong> Falling rocks.</p>
<!-- Stylistically offset (non-semantic) -->
<p>This recipe calls for <b>bacon</b> and <b>baconnaise</b>.</p>
```

### Italicize Text with Emphasis
Semantic inline element for stressed emphasis or alternative tone.
```html
<!-- Stressed emphasis -->
<p>I <em>love</em> Chicago!</p>
<!-- Alternative voice or tone (non-semantic) -->
<p>The name <i>Shay</i> means a gift.</p>
```

## Building Structure
HTML5 introduced semantic elements to better organize content:
- **`<header>`**: Represents the top of a page, section, or article. Distinct from `<head>` (metadata) and `<h1>`–`<h6>` (headings).
- **`<nav>`**: Contains navigational links, such as global navigation, table of contents, or previous/next links.
- **`<article>`**: Defines independent, self-contained content that can be distributed or reused.
- **`<section>`**: Groups thematically related content.
- **`<aside>`**: Represents sidebars, inserts, or brief explanations (block-level).
- **`<footer>`**: Closes a page, article, or section, often containing metadata or links.

### Deciding Between `<article>`, `<section>`, or `<div>` Elements
- Use `<article>` for standalone content (e.g., a blog post).
- Use `<section>` for thematic grouping within a larger context.
- Use `<div>` for non-semantic grouping, typically for styling purposes.

## Encoding Special Characters
Special characters (e.g., `&`, `<`, `>`) must be encoded to display correctly. Use resources like [CopyPasteCharacter](http://copypastecharacter.com/) for reference.

## Creating Hyperlinks
Hyperlinks (`<a>`) connect to other pages, files, or parts of the same page.
```html
<a href="http://shayhowe.com">Shay</a>
```

### Relative & Absolute Paths
- **Relative Path**: Links to a file within the same site.
  ```html
  <a href="about.html">About</a>
  ```
- **Absolute Path**: Links to an external URL.
  ```html
  <a href="http://www.google.com/">Google</a>
  ```

### Linking to an Email Address
```html
<a href="mailto:shay@awesome.com?subject=Reaching%20Out&body=How%20are%20you">Email Me</a>
```

### Opening Links in a New Window
Use `target="_blank"` to open links in a new tab.
```html
<a href="http://shayhowe.com/" target="_blank">Shay Howe</a>
```

### Linking to Parts of the Same Page
Use `id` attributes to link to specific sections.
```html
<body id="top">
  ...
  <a href="#top">Back to top</a>
  ...
</body>
```

## Practice
Example HTML structure for a conference website:
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>Styles Conference</title>
    <link rel="stylesheet" href="./assets/stylesheets/main.css">
  </head>
  <body>
    <header>
      <h1><a href="index.html">Styles Conference</a></h1>
      <h3>August 24–26th — Chicago, IL</h3>
      <nav>
        <a href="index.html">Home</a>
        <a href="speakers.html">Speakers</a>
        <a href="schedule.html">Schedule</a>
        <a href="venue.html">Venue</a>
        <a href="register.html">Register</a>
      </nav>
    </header>
    <section>
      <h2>Dedicated to the Craft of Building Websites</h2>
      <p>Every year the brightest web designers and front-end developers descend on Chicago to discuss the latest technologies. Join us this August!</p>
      <a href="register.html">Register Now</a>
      <section>
        <a href="speakers.html">
          <h5>Speakers</h5>
          <h3>World-Class Speakers</h3>
        </a>
        <p>Joining us from all around the world are over twenty fantastic speakers, here to share their stories.</p>
      </section>
    </section>
    <p>Every year the brightest web designers and front-end developers descend on Chicago to discuss the latest technologies. Join us this August!</p>
    <footer>
      <small>© Styles Conference</small>
      <nav>
        <a href="index.html">Home</a>
        <a href="speakers.html">Speakers</a>
        <a href="schedule.html">Schedule</a>
        <a href="venue.html">Venue</a>
        <a href="register.html">Register</a>
      </nav>
    </footer>
  </body>
</html>
```
