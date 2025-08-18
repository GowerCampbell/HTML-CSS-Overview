# Extending Semantics & Accessibility

Designing your html you want to write semantic and accessible code that machines can interpret. Do not use meaningless element, when a semantic one can add value to your code through microdata & WAI-ARIA. Be an advocate for semantics and accessibility. Outline goals & objectives within your code..

-----

## Semantic Motivation

Retain your integrity and write the best code possible, for semantics provide larger meaning. Link: [https://vanseodesign.com/web-design/semantic-html/](https://vanseodesign.com/web-design/semantic-html/)

**Clean | Accessible | Search Engine Friendly | User Interface**

Defined information can can help make assistive technologies to serve the content, making it easier to exchange and use information across platforms.

-----

## Structural & Text-Level Semantics

Using the `header`, `nav`, `article`, `section`, `aside` and `footer` elements to provide additional context to content. When you outline and structure pages. Link:[https://learn.shayhowe.com/html-css/getting-to-know-html/](https://learn.shayhowe.com/html-css/getting-to-know-html/)

### Hiding Content

With the `display: none;` css declration you hide and show content, creating hidden messages. Consider the hidden boolean attribute that can used within an element. Screen readers, and other devices will recognize this.

```html
<div hidden>...</div>

<div style="display: none;">...</div>
```

### Bolding Text (`<b>` or `<strong>`)

The `<b>` or `<strong>` have different semantic meaning. The `<strong>` element outlines a text with a strong importance. The `<b>` element identifies text that is stylistically offset without importance.

```html
<strong>Caution:</strong> Falling rocks.

This recipe calls for <b>bacon</b> and <b>baconnaise</b>.
```

### Italicizing Text (`<em>` or `<i>`)

The `<em>` and `<i>` have different italic meanings. The `<em>` element places a stressed emphasis on text, while the `<i>` element identifies an alternate voice or tone.

```html
I <em>love</em> Chicago!

The name <i>Shay</i> means a gift.
```

The `<i>` element is often used as a hook for icons in frameworks like Bootstrap.

### Underlining Text (`<ins>` or `<u>`)

Different sematic meaning is used when underlining. The `<ins>` element is used to identify text that has been recently added to the document. The `<u>` element simply refers unarticulated annotation. REMEMBER Underlining is not a hyperlink.

```html
<ins cite="http://learn.shayhowe.com" datetime="2012-07-01">
 Updated: This website now contains an advanced guide.
</ins>

<u>Urushihara Yuuji</u> won <u>Sasuke 27</u>.
```

### Striking Text (`<del>` or `<s>`)

The `<del>` is used to identify deleted or removed text. The `<s>` is used for content that is no longer accurate or relevant.

```html
I am an avid cyclist, <del cite="http://shayhowe.com" datetime="2012-07-01">skateboarder</del> and designer.

<s>$24.99</s> $19.99
```

### Other Text Elements

  * **Highlighting Text `<mark>`**: Specifically for reference purpose without having to use an un-semantic text level element.
    `Search results for <mark>'chicago'</mark>.`

  * **Abbreviations `<abbr>`**: Used alongside the `title` attribute.
    `<abbr title="HyperText Markup Language">HTML</abbr>`

  * **Sub & Superscripts (`<sub>` & `<sup>`)**: Reserved for typographical conventions.
    `H<sub>2</sub>O` and `1<sup>st</sup> Place`

  * **Meter & Progress**: To gauge scale you can use the `<meter>` element to measure a fixed value, while the `<progress>` element to progress the increasing measurement.

    ```html
    <meter value="7" max="10">7 stars</meter>

    You are <progress value="50" max="100">50%</progress> complete.
    ```

  * **Time & Address**: Use `<time>` (with a `datetime` attribute for machines) and `<address>` for contact info.

    ```html
    <time datetime="2011-08-24T15:00">August 24th, 2011 at 3pm</time>
    ```

  * **Presenting Code (`<pre>` & `<code>`)**: Use `<code>` for inline code and wrap it in `<pre>` for larger blocks.

    ```html
    <pre><code>body {
     color: #666;
     font: 14px/20px Arial, sans-serif;
    }</code></pre>
    ```

  * **Citations & Quotes**: Use `<cite>` for a work's title, `<q>` for short inline quotes, and `<blockquote>` for longer, block-level quotations.

    ```html
    <blockquote cite="http://example.com">
     <p>“Design is the fundamental soul of a human-made creation...”</p>
     <p><cite>— Steve Jobs</cite></p>
    </blockquote>
    ```

### Hyperlink Attributes

The `<a>` tag has useful attributes beyond `href`:

  * **`download`**: A boolean attribute that prompts the browser to download the linked file.
    `<a href="twitter-logo.png" download>Twitter Logo</a>`
  * **`rel`**: Identifies the relationship between the current document and the linked one.
    `<a href="legal.html" rel="copyright">Terms of Use</a>`

-----

## Microdata

HTML can be extended with nested groups of name-value pairs that allow machines to pick up additional semantics and information for rich content.
Link: [https://schema.org/docs/schemas.html](https://schema.org/docs/schemas.html)

### Outlining Microdata

Microdata is identified by three main attributes: `itemscope`, `itemtype`, and `itemprop`.

1.  **`itemscope`**: A boolean attribute that declares the scope of the microdata item. It's placed on the parent element.
2.  **`itemtype`**: Identifies the microdata vocabulary used (e.g., `http://schema.org/Person`).
3.  **`itemprop`**: Determines what property is being referenced. The content within the element becomes the value of that property.

<!-- end list -->

```html
<section itemscope itemtype="http://schema.org/Person">
 <h1 itemprop="name">Shay Howe</h1>
 <div itemprop="jobTitle">Designer and Front-end Developer</div>
 <img src="shay.jpg" itemprop="image" alt="Shay Howe">
 <a href="http://www.shayhowe.com" itemprop="url">shayhowe.com</a>
</section>
```

-----

## WAI-ARIA

WAI-ARIA (Web Accessibility Initiative - Accessible Rich Internet Applications) helps those with disabilities by using syntax to define a `role` (what a block of content can do) and `states` (how it's configured).

### Roles

Roles help specify what certain elements and blocks of content do on a page. **Landmark Roles** are key for page navigation:

  * `application`
  * `banner` (for the main `<header>`)
  * `complementary` (for an `<aside>`)
  * `contentinfo` (for the main `<footer>`)
  * `form`
  * `main`
  * `navigation` (for a `<nav>`)
  * `search`

<!-- end list -->

```html
<header role="banner">
 <nav role="navigation">...</nav>
</header>

<main>
 <article role="article">
  <section role="region">...</section>
 </article>
</main>

<aside role="complementary">...</aside>

<footer role="contentinfo">...</footer>
```

### States & Properties

These attributes provide information about the current state of an element to assistive technologies (e.g., `aria-hidden`, `aria-required`).
Link: [https://www.w3.org/TR/wai-aria/\#states\_and\_properties](https://www.w3.org/TR/wai-aria/#states_and_properties)

-----

## Questions and Answers

\<details\>
\<summary\>Question 1: What is the difference between the \<code\>\&lt;strong\&gt;\</code\> and \<code\>\&lt;b\&gt;\</code\> elements in HTML?\</summary\>
\<p\>The \<code\>\&lt;strong\&gt;\</code\> element indicates text with strong importance, often rendered in bold, emphasizing its significance. The \<code\>\&lt;b\&gt;\</code\> element is used for text that is stylistically offset, also typically bold, but without conveying importance, such as for visual distinction.\</p\>
\</details\>

\<details\>
\<summary\>Question 2: How does the \<code\>\&lt;em\&gt;\</code\> element differ from the \<code\>\&lt;i\&gt;\</code\> element in terms of semantic meaning?\</summary\>
\<p\>The \<code\>\&lt;em\&gt;\</code\> element places a stressed emphasis on text, indicating importance or urgency, typically rendered in italics. The \<code\>\&lt;i\&gt;\</code\> element identifies text in an alternate voice or tone, such as foreign words or names, also italicized, but without implying emphasis.\</p\>
\</details\>

\<details\>
\<summary\>Question 3: What is the purpose of the \<code\>hidden\</code\> attribute, and why is it preferred over CSS \<code\>display: none\</code\> for accessibility?\</summary\>
\<p\>The \<code\>hidden\</code\> attribute is a boolean attribute that hides an element from all users, including screen readers, ensuring it is not interpreted by assistive technologies. It is preferred over CSS \<code\>display: none\</code\> because it is a semantic HTML attribute that explicitly communicates the hidden state to all devices and assistive technologies, improving accessibility.\</p\>
\</details\>

\<details\>
\<summary\>Question 4: What are the roles of the \<code\>\&lt;meter\&gt;\</code\> and \<code\>\&lt;progress\&gt;\</code\> elements, and how do their attributes differ?\</summary\>
\<p\>The \<code\>\&lt;meter\&gt;\</code\> element measures a fixed value within a defined range, using attributes like \<code\>min\</code\>, \<code\>max\</code\>, \<code\>low\</code\>, \<code\>high\</code\>, \<code\>optimum\</code\>, and \<code\>value\</code\> to represent static measurements. The \<code\>\&lt;progress\&gt;\</code\> element indicates the completion progress of a task, using \<code\>value\</code\> and \<code\>max\</code\> attributes to show how much has been completed relative to the total.\</p\>
\</details\>

\<details\>
\<summary\>Question 5: How does the \<code\>itemscope\</code\> attribute contribute to microdata, and what is its relationship with \<code\>itemtype\</code\> and \<code\>itemprop\</code\>?\</summary\>
\<p\>The \<code\>itemscope\</code\> attribute declares the scope of a microdata item, marking the parent element containing related microdata. The \<code\>itemtype\</code\> attribute specifies the microdata vocabulary (e.g., from Schema.org), defining the type of item, such as Person or Event. The \<code\>itemprop\</code\> attribute identifies specific properties within the scope, with the element’s content or attributes (e.g., \<code\>href\</code\>, \<code\>src\</code\>) providing the property’s value.\</p\>
\</details\>

\<details\>
\<summary\>Question 6: What are WAI-ARIA roles, and how do they enhance accessibility for HTML elements like \<code\>header\</code\> and \<code\>nav\</code\>?\</summary\>
\<p\>WAI-ARIA roles define the purpose or behavior of elements (e.g., \<code\>banner\</code\> for header, \<code\>navigation\</code\> for nav), enhancing accessibility by providing additional context to assistive technologies. They help screen readers and other tools understand the structure and functionality of content, especially for dynamic or complex interfaces, ensuring better navigation and interaction for users with disabilities.\</p\>
\</details\>
