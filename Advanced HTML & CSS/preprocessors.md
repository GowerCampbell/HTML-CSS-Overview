# Preprocessors

Take one type of data type and converts it to another using:
Haml into HTML (https://haml.info/)
Sass into CSS (https://sass-lang.com/)

Empower HTML & CSS by removing ineffiences making building websites easier and more logical/

## Haml
Also known as HTML abstraction markup language, writing beautiful markup, proccessed by 
HTML and promotes DRY and structured markup.

Installation (ruby libary installed)
gem install haml

Files written in haml become .haml and are converted to html once compiled.
haml index.haml index.html

Use haml --help to see available options. 
Does not let you watch a file or directory for changes..

Inside of a rails application (A web app written using Ruby) a Haml is added to a GEML 

Mac CodeKit: https://codekitapp.com/

## Doctype
writing a document in Haml is knowing what type of Doctype is to used. When working 
with HTML files use <!DOCTYPE html> for HTML5 while Haml document types use !!! 5

## Declaring Elements
HTML use opening and closing tags while hamel only needs the opening with a %

%body
  %header
    %h1 Hello World
  %section
    %p Lorem ipsum dolor sit amet.
 
What is important is the indentation to identify nesting.
 
<body>
  <header>
    <h1>Hello World</h1>
  </header>
  <section>
    <p>Lorem ipsum dolor sit amet.</p>
  </section>
</body>

### Handling text must be on the same line as the declared or indented element. 
It cannot be nested below

## Attributes
The attributes are declatred after the element in either {} or () using Ruby 0r HTML syntax/
HAML
%img{:src => "shay.jpg", :alt => "Shay Howe"}
%img{src: "shay.jpg", alt: "Shay Howe"}
%img(src="shay.jpg" alt="Shay Howe")

HTML

<img src="shay.jpg" alt="Shay Howe">

## Classes & IDs 
Are declared the same with a . or a # but they can be treated different:
HAML
%section.feature
%section.feature.special
%section#hello
%section#hello.feature(role="region")
HTML
<section class="feature"></section>
<section class="feature special"></section>
<section id="hello"></section>
<section class="feature" id="hello" role="region"></section>


## Division Classes & ID
In the event a class or ID is used on a %div or a <div> it may be imitted and
the class or ID can be used outright

Haml
.awesome
.awesome.lesson
#getting-started.lesson

Compiled HTML
<div class="awesome"></div>
<div class="awesome lesson"></div>
<div class="lesson" id="getting-started"></div>

## Boolean Attributes
Handled within RUBY or HTML depending on syntax
HAML
%input{:type => "checkbox", :checked => true}
%input(type="checkbox" checked=true)
%input(type="checkbox" checked)
HTML
<input type="checkbox" checked>

## Escaping Text
One of the benefits of Haml is the ability to evaluate and run Ruby.

But it is mostly used to help code escape using the \ allowung text text to be renderered
without being executed.
Haml
.author
  = @author
  \= @author

HTML 
<div class="author">
  Shay Howe
  = @author
</div>

## Text Escaping Alternatives
Including a period directly after a link that is not part of the anchor line.
HTML
<p>Shay is <a href="#">awesome</a>.</p>

You can add a backslash before the period that will escape the character allowing uou 
place a blank space between the last word and the period but not give you the desired look.

%p
  Shay is
  = succeed "." do
    %a{:href => "#"} awesome

## Comments
While <!-- sets up a html comment --> haml uses / the forward slash to set a line
to be used for commented parts
Haml
%div
  / Commented line
  Actual line

/
  %div
    Commented block

HTML 
<!--[if lt IE 9]>
  <script src="html5shiv.js"></script>
<![endif]-->

## Silent Comments
Haml provides the ability to create Haml specfic comments, letting them differ from general HTML comments in that 
upon being complued any content with a silent comment is removed from the page. 

%div
  -# Removed line
  Actual line

<div>
  Actual line
</div>

## Filters 
Allowing for different input types to be used inside Haml using a : colon of the filter 
:markdown for example, with all the content to be filtered and nested underneath.

## Common Filters
With the more popular ones of the group being :css or :javascript
:cdata
:coffee
:css
:erb
:escaped
:javascript 
:less
:markdown
:maruku
:plain
:preserve
:ruby
:sass
:scss
:textile

Javascript Filter
Haml
:javascript
    $('button').on('click', function(event) {
       $('p').hide('slow');
  });
HTML
<script>
  $('button').on('click', function(event) {
    $('p').hide('slow');
  }); 
</script>
Haml
:css 
  .container {
    margin: 0 auto;
    width: 960px;
  }

  :sass
  .container
    margin: 0 auto
    width: 960px

HTML
<style>
  .container {
    margin: 0 auto;
    width: 960px;
  }
</style>

## Ruby Interpolation
Haml can evaluate Ruby used within the text. You wrap the necessary Ruby code inside

Haml
%div{:class => "student-#{@student.name}"}

HTML 
<div class="student-shay">

## SCSS & Sass
Preprocessing languges used  alonglide Haml that make code writing easy and leverage ruby in your code.
Known as Syntactically Awersome Stylesheets and can come with a strict indented syntax

## Installation
SCSS and Sass are complied using Ruby to produce CSS files
gem install sass
and will use .scss or sass file which will convert to .css:
sass styles.sass styles.css

Excuted within the the directory from which the command is run, should the files reside outside of the directory their path 
needs to be explicitly stated within the command.

Should changes to a file be ongoing Sass can watch the file, recompile the css every time a change takes place:
sass --watch styles.sass:styles.css

Additionally compiling or watching individual files, Sass is capable of watching entire directories of files
and converting them into css:
sass --watch assets/sass:public/css

### Converting Files from SCSS to Sass vice versa
# Convert Sass to SCSS
sass-convert styles.sass styles.scss

# Convert SCSS to Sass
sass-convert styles.scss styles.sass

## Syntax
The only difference is severity and syntax of SCSS is not much different from regular CSS and standard css will run inside SCSS

However, Sass is fairly strict and any indenting or character errors will the styles from compiling, while omiting {} curly brackets and semicolons ;

SCSS
.new {
  color: #ff7b29;
  font-weight: bold;
  span {
    text-transform: uppercase;
  }
}

Sass
.new
  color: #ff7b29
  font-weight: bold
  span
    text-transform: uppercase

CSS

.new {
  color: #ff7b29;
  font-weight: bold;
}
.new span {
  text-transform: uppercase;
}

## SCSS vs Sass
Personal preference and is based on a specific team or project. 
Because Sass requires less characters and gives cleaner syntax, Sass will not allow
straight CSS iput.


## Nesting
Notice gow the selectors maybe be nested inside onre another to create compound selectors. 

Do **NOT** nest selectors for unapparent reasons or go overboard nesting:

Sass.
portfolio
  border: 1px solid #9799a7
  ul
    list-style: none
  li
    float: left

CSS

.portfolio {
  border: 1px solid #9799a7;
}
.portfolio ul {
  list-style: none;
}
.portfolio li {
  float: left;
}

## Nesting Properties

From font, margin, padding or border properties. 

Sass
div
  font:
    family: Baskerville, Palatino, serif
    style: italic
    weight: normal

CSS
div {
  font-family: Baskerville, Palatino, serif;
  font-style: italic;
  font-weight: normal;
}

## Nested Media Queries
Individual Media queries may be nested inside a selector, changing propert values based 
off a media condition 
Sass
.container
  width: 960px
  @media screen and (max-width: 960px)
    width: 100%
CSS
.container {
  width: 960px;
}
@media screen and (max-width: 960px) {
  .container {
    width: 100%;
  }
}

## Parent Selector
Adding a style that effects the type, class or id we can use an ampersand, & in conjunction with a 
pseudo-class OR used to bind additional selectors to its its parent as &.featured.

Sass
a 
  color: #0087cc
  &:hover
    color: #ff7b29
CSS
a {
  color: #0087cc;
}
 a:hover {
  color: #ff7b29;
}
## Parent Key Selector
Adding qualifying selectors to make compound selectors.
Sass
.btn
  background: linear-gradient(#fff, #9799a7)
  .no-cssgradients &
    background: url("gradient.png") 0 0 repeat-x
CSS
.btn {
  background: linear-gradient(#fff, #9799a7);
}
.no-cssgradients .btn {
  background: url("gradient.png") 0 0 repeat-x;
}

## Comments
Sass handles comments similar to that of Haml using /*...*/ for both.
However, be aware there is a syntax for "silient comments" 
Sass
/* Normal comment */
div
  background: #333
// Omitted comment
strong
  display: block
CSS
/* Normal comment */
div {
  background: #333;
}

strong {
  display: block;
}
## Variables
Sass allows us to define and store varibles defined by a $ sign and a :
From a number, string, color or boolean, null or even a list of values.
Sass
$font-base: 1em
$serif: "Helvetica Neue", Arial, "Lucida Grande", sans-serif

p
  font: $font-base $serif

CSS
p {
  font: 1em "Helvetica Neue", Arial, "Lucida Grande", sans-serif;
}

## Variable Interpolation
It can be used anywhere inside a Sass document giving you a class name, property and a string of text
Sass
$location: chicago
$offset: left

.#{$location}
  #{$offset}: 20px

CSS
.chicago {
  left: 20px;
}

## Calculations
We can then do calculations in a variety of different manners to handle problems such as addition, subtraction, division, multiplication and rounding.

Tied to an equation with operators

Sass
width: 40px + 6
width: 40px - 6
width: 40px * 6
width: 40px % 6

CSS
width: 46px;
width: 34px;
width: 240px;
width: 4px;

## Division
The value resides in that unit
Sass
width: 100px / 10
width: (100px / 10)
width: (100px / 10px)
$width: 100px
width: $width / 10
width: 5px - 100px / 10
CSS
width: 100px/10;
width: 10px;
width: 10;
width: 10px;
width: -5px;

## Detailed Math
Math operations based on parentheses
Sass
$grid: 16
$column: 40px
$gutter: 20px
$container: ($column * $grid) + ($gutter * $grid)

width: $container

CSS
width: 960px;

## Number Functions 
default Sass allows us to manipulate number values as we wish.
Sass
width: percentage(2.5) /* Turns value into % */
width: round(2.5px) /* rounds a value to the closest number, defaulting up */
width: ceil(2.5px) /* rounds a value up to the closest whole number */
width: floor(2.5px) /* rounds a value down to closest whole number */
width: abs(-2.5px) /* finds absolute value of a given number */

CSS
width: 250%;
width: 3px;
width: 3px;
width: 2px;
width: 2.5px;

## Color
Sass provides a better assistance with working with colors, providing a handeful of features to alter and manipulate colors.
Sass
color: rgba(#8ec63f, .25)

$green: #8ec63f
color: rgba($green, .25)

CSS
color: rgba(142, 198, 63, .25);

## Color Operations
Colors using addition, subtraction, multipication and division/

Performed the red, green, blue components.
Sass
color: #8ec63f + #666
color: #8ec63f * 2
color: rgba(142, 198, 63, .75) / rgba(255, 255, 255, .75)
CSS
color: #f4ffa5;
color: #ffff7e;
color: rgba(0, 0, 0, .75);

## Color Alterations
Color operators are helpful for inverse colores, complementary blends, mixing two colors together and find the grayscale value of a color
Sass
color: invert(#8ec63f)
color: complement(#8ec63f)
color: mix(#8ec63f, #fff)
color: mix(#8ec63f, #fff, 10%)
color: grayscale(#8ec63f)
CSS
color: #7139c0;
color: #773fc6;
color: #c6e29f;
color: #f3f9eb;
color: #838383;

## HSLa Color Alterations
Adding more alterations to HSLa color
Sass
color: lighten(#8ec63f, 50%)
color: darken(#8ec63f, 30%)
color: saturate(#8ec63f, 75%)
color: desaturate(#8ec63f, 25%)
color: adjust-hue(#8ec63f, 30)
color: adjust-hue(#8ec63f, -30)
color: fade-in(rgba(142, 198, 63, 0), .4)
color: fade-out(#8ec63f, .4)

CSS
color: white;
color: #3b5319;
color: #98ff06;
color: #89a75e;
color: #4ac63f;
color: #c6bb3f;
color: rgba(142, 198, 63, 0.4);
color: rgba(142, 198, 63, 0.6);

## Color Manipulation

