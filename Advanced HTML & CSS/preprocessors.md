# Preprocessors

A preprocessor takes one data type and converts it to another. For web development, this often means converting a more powerful, developer-friendly language into standard HTML and CSS. They empower HTML & CSS by removing inefficiencies, making building websites easier and more logical.

- **Haml** compiles into **HTML**.
- **Sass/SCSS** compiles into **CSS**.

## Haml

**Haml** (HTML Abstraction Markup Language) is a preprocessor for writing clean, structured, and beautiful markup. It promotes the **DRY** (Don't Repeat Yourself) principle and compiles directly into HTML.

<details>
<summary>How do you install and compile Haml?</summary>

Haml is a Ruby library. You can install it using the following command:

```bash
gem install haml
```

To compile a `.haml` file into an `.html` file, you run:

```bash
haml index.haml index.html
```

Haml doesn't natively watch files for changes, so tools like **CodeKit** on Mac are often used to automate compilation. In a **Ruby on Rails** application, you would simply add Haml to your project's `Gemfile`.

</details>

### Haml Syntax

<details>
<summary>How do you declare a DOCTYPE in Haml?</summary>

Instead of `<!DOCTYPE html>`, you use `!!!` for a standard HTML5 doctype.

```haml
!!! 5
```

</details>

<details>
<summary>How do you declare elements and handle nesting?</summary>

Instead of opening and closing tags, you declare an element with a `%` symbol. **Indentation is crucial** as it defines the nesting structure.

**Haml:**

```haml
%body
  %header
    %h1 Hello World
  %section
    %p Lorem ipsum dolor sit amet.
```

**Compiled HTML:**

```html
<body>
  <header>
    <h1>Hello World</h1>
  </header>
  <section>
    <p>Lorem ipsum dolor sit amet.</p>
  </section>
</body>
```

Text must be on the same line as the element declaration or properly indented on the next line.

</details>

<details>
<summary>How are attributes assigned to elements?</summary>

Attributes are declared after the element using either curly braces `{}` (Ruby hash syntax) or parentheses `()` (HTML-like syntax).

**Haml:**

```haml
%img{:src => "shay.jpg", :alt => "Shay Howe"}
%img{src: "shay.jpg", alt: "Shay Howe"}
%img(src="shay.jpg" alt="Shay Howe")
```

**Compiled HTML:**

```html
<img src="shay.jpg" alt="Shay Howe">
```

</details>

<details>
<summary>What is the shortcut for declaring classes and IDs?</summary>

Classes (`.`) and IDs (`#`) are declared directly after the element tag, similar to CSS selectors.

**Haml:**

```haml
%section.feature.special
%section#hello
%section#hello.feature(role="region")
```

**Compiled HTML:**

```html
<section class="feature special"></section>
<section id="hello"></section>
<section class="feature" id="hello" role="region"></section>
```

</details>

<details>
<summary>Is there a shortcut for `div` elements with a class or ID?</summary>

Yes. If you need a `<div>`, you can omit the `%div` and start directly with the class or ID.

**Haml:**

```haml
.awesome
#getting-started.lesson
```

**Compiled HTML:**

```html
<div class="awesome"></div>
<div class="lesson" id="getting-started"></div>
```

</details>

<details>
<summary>What are the two types of comments in Haml?</summary>

- **HTML Comment (`/`):** A forward slash creates a standard HTML comment that will appear in the compiled HTML.
- **Silent Comment (`-#`):** A hyphen and hash create a silent comment that is completely removed during compilation and does not appear in the final HTML.

**Haml:**

```haml
/ This is an HTML comment.
-# This is a silent comment.
```

**Compiled HTML:**

```html
<!-- This is an HTML comment. -->
```

</details>

<details>
<summary>What are Haml filters and what are they used for?</summary>

Filters allow you to embed other languages directly within a Haml file. You declare a filter with a colon (`:`), and all indented content below it will be processed by that filter. Common filters include `:javascript`, `:css`, `:markdown`, and `:sass`.

**Haml:**

```haml
:javascript
  $('button').on('click', function(event) {
    $('p').hide('slow');
  });

:css
  .container {
    margin: 0 auto;
    width: 960px;
  }
```

**Compiled HTML:**

```html
<script>
  $('button').on('click', function(event) {
    $('p').hide('slow');
  });
</script>
<style>
  .container {
    margin: 0 auto;
    width: 960px;
  }
</style>
```

</details>

<details>
<summary>How can you embed Ruby code directly into Haml?</summary>

**Ruby Interpolation** allows you to evaluate Ruby code within an attribute or text by wrapping it in `#{...}`.

**Haml:**

```haml
%div{:class => "student-#{@student.name}"}
  Welcome, #{@student.name}!
```

**Compiled HTML (assuming `@student.name` is "shay"):**

```html
<div class="student-shay">
  Welcome, Shay!
</div>
```

</details>

## SCSS & Sass

**Sass** (Syntactically Awesome Stylesheets) is a CSS preprocessor that adds powerful features like variables, nesting, and mixins. It has two syntaxes: **SCSS** and the original indented syntax, **Sass**.

<details>
<summary>How do you install and compile Sass?</summary>

Sass is also a Ruby gem.

```bash
# Install Sass
gem install sass

# Compile a single file
sass styles.sass styles.css

# Watch a file for changes and recompile automatically
sass --watch styles.sass:styles.css

# Watch an entire directory
sass --watch assets/sass:public/css
```

</details>

<details>
<summary>What is the key syntactical difference between SCSS and Sass?</summary>

- **SCSS (.scss):** Uses curly braces `{}` and semicolons `;`, just like standard CSS. In fact, any valid CSS is also valid SCSS.
- **Sass (.sass):** Uses indentation to define nesting and newlines to separate properties. It omits braces and semicolons for a cleaner, more minimal syntax.

**SCSS:**

```scss
.new {
  color: #ff7b29;
  font-weight: bold;
  span {
    text-transform: uppercase;
  }
}
```

**Sass:**

```sass
.new
  color: #ff7b29
  font-weight: bold
  span
    text-transform: uppercase
```

</details>

### Sass Features

<details>
<summary>How does nesting work in Sass?</summary>

You can nest selectors inside one another to create compound selectors, which helps organize your styles and mirrors your HTML structure. You can also nest properties like `font` or `border`.

**Sass Nesting:**

```sass
.portfolio
  border: 1px solid #9799a7
  ul
    list-style: none
  li
    float: left

  // Property Nesting
  font:
    family: Baskerville, serif
    style: italic
```

**Compiled CSS:**

```css
.portfolio {
  border: 1px solid #9799a7;
  font-family: Baskerville, serif;
  font-style: italic;
}
.portfolio ul {
  list-style: none;
}
.portfolio li {
  float: left;
}
```

</details>

<details>
<summary>What is the parent selector `&` used for?</summary>

The ampersand `&` refers to the parent selector. It's most commonly used for applying pseudo-classes like `:hover` or for adding a qualifying class to the parent.

**Sass:**

```sass
a
  color: #0087cc
  &:hover
    color: #ff7b29

.btn
  // Prepends .no-cssgradients to .btn
  .no-cssgradients &
    background: url("gradient.png")
```

**Compiled CSS:**

```css
a {
  color: #0087cc;
}
a:hover {
  color: #ff7b29;
}
.no-cssgradients .btn {
  background: url("gradient.png");
}
```

</details>

<details>
<summary>How do you declare and use variables?</summary>

Variables store reusable values like colors, fonts, or measurements. They are declared with a `$` sign. You can also use **variable interpolation** `#{...}` to use a variable's value within a selector or property name.

**Sass:**

```sass
// Variable Declaration
$primary-color: #ff7b29
$base-font: "Helvetica Neue", Arial, sans-serif

// Variable Usage
body
  font-family: $base-font
  color: $primary-color

// Interpolation
$location: chicago
.#{$location}
  background: $primary-color
```

</details>

<details>
<summary>What is the difference between `@extend` and a `@mixin`?</summary>

- **`@extend`:** Is used to share sets of CSS properties from one selector to another. It groups the extending selectors together in the compiled CSS, keeping the code DRY. It is best for sharing **static** style sets.
- **`@mixin`:** Is like a function that can take arguments to create reusable blocks of styles. It's ideal for creating **dynamic** styles or for vendor prefixing, where you need to repeat a block of code with slight variations.

**Extend Example:**

```sass
%alert
  padding: 10px 20px
  border-radius: 10px

.alert-error
  @extend %alert
  background: #f2dede
```

**Mixin Example:**

```sass
@mixin box-shadow($shadow...)
  -webkit-box-shadow: $shadow
  box-shadow: $shadow

.card
  @include box-shadow(0 1px 3px rgba(0,0,0,0.2))
```

</details>

<details>
<summary>How do you manage multiple files with Sass?</summary>

The `@import` directive allows you to import multiple `.scss` or `.sass` files (often called "partials") into a single main file. This helps organize your code into logical modules (e.g., `_variables.scss`, `_grid.scss`, `_typography.scss`) without creating extra HTTP requests.

**Sass:**

```sass
// In styles.scss
@import "normalize"
@import "grid", "typography"
```

</details>

<details>
<summary>How do control directives like loops and conditionals work?</summary>

Sass includes logic for more advanced styling.

- **`@if`:** Applies styles based on a condition, similar to `if/else` statements in other languages.
- **`@for`:** Outputs styles in a loop based on a counter variable.
- **`@each`:** Loops through each item in a list and applies a style.
- **`@while`:** Continues to output styles until a statement becomes false.

**`@for` Loop Example:**

```sass
@for $col from 1 through 4
  .col-#{$col}
    width: (100% / 4) * $col
```

</details>

<details>
<summary>How does Sass handle colors and color functions?</summary>

Sass provides a suite of functions to manipulate colors. You can programmatically `lighten`, `darken`, `saturate`, `desaturate`, `mix`, and `adjust` colors.

**Sass:**

```sass
$brand-color: #8ec63f

.button
  background: $brand-color
  &:hover
    background: lighten($brand-color, 10%)

.text
  color: complement($brand-color)
```

**Compiled CSS:**

```css
.button {
  background: #8ec63f;
}
.button:hover {
  background: #a5d36b;
}
.text {
  color: #773fc6;
}
```

</details>

### Other Preprocessors & Resources

While Haml and Sass are popular choices that fit well into a Ruby on Rails ecosystem, other tools may be better for your project or team.

- **HTML/Templating:** Slim, Jade (now Pug)
- **CSS/Styling:** Less
- **JavaScript:** CoffeeScript

When choosing a preprocessor, consider what will work best for your team's skillset and the project's technology stack (e.g., a Node.js project might benefit from Pug and Less).

#### Resources & Links

- [Haml Reference](https://haml.info/docs/yardoc/file.REFERENCE.html)
- [Sass Documentation](https://sass-lang.com/documentation/)
- [Sass Modules](https://sass-lang.com/documentation/modules/)

