Working with Typography
The ability to embed fonts, giving us a palette of styles to add to an website.

Typeface vs. Font
Typeface is what we see?
A Font is a file that contains a typeface? 

Adding color to a text?

html {
  color: #555;
}

Sets the color of all the text within the element.

Changing Font Propertires?
CSS offers a lot of different properties
Font-x Text-x Based

Font Based Properties

Declare a font and its fallback or substitute fonts
body {
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
}

Ability to set the size of the using common length values, pixrls em units, percentages, points or font-size keywords
body {
  font-size: 14px;
}

Accepting noirmal, italic, oblique and inherit keywords
.special {
  font-style: italic;
}

Set to small capitals or small caps as a varient 
Accepts: normal, small-caps or inherit
firm {
  font-variant: small-caps;
}

changing the specfic weight of a typeface: normal, bold, bolder, lighter or inherit.
.daring {
  font-weight: bold;
}
Better to use numeric values: 100, 200, 300, 400, 500, 600, 700, 800, and 900 pertain specifically to typefaces that have multiple weights.
.daring {
  font-weight: 600;
}
Creating semibold typeface depending on font.

If ussed on a baseline line grid use pixels. And can be accomplished by setting the line-height by either 150% or 1.5
body {
  line-height: 22px;
}

Included can be used to center a line of text within an element.
.btn {
  height: 22px;
  line-height: 22px;
}

Shorthand Font Properties
Can be read by left to right: font-style, font-variant, font-weight, font-size, line-height, and font-family.
html {
  font: italic small-caps bold 14px/22px "Helvetica Neue", Helvetica, Arial, sans-serif;
}

Font properties All Together

<h2><a href="#">I Am a Builder</a></h2>

<p class="byline">Posted by Shay Howe</p>

<p>Every day I see designers and developers working alongside one another. They work intelligently in pursuit of business objectives. They work diligently making exceptional products. They solve real problems and take pride in their work. They are builders. <a href="#">Continue&#8230;</a></p>

h2,
p {
  color: #555;
  font: 13px/20px "Helvetica Neue", Helvetica, Arial, sans-serif;
}
a {
  color: #0087cc;
}
a:hover {
  color: #ff7b29;
}
h2 {
  font-size: 22px;
  font-weight: bold;
  margin-bottom: 6px;
}
.byline {
  color: #9799a7;
  font-family: Georgia, Times, "Times New Roman", serif;
  font-style: italic;
  margin-bottom: 18px;
}

 :hover pseudo-class styles an element when a user hovers over that element lets it change color.

<!DOCTYPE html>
<html lang="en">
  <head>
  <meta charset="utf-8">
  <title>Styles Conference</title>
  <link rel="stylesheet" href="./assets/stylesheets/main.css">
</head>
  <body>
  <header class="container group">
  <section class="container" >
    <h1 class="logo">
  <a href="index.html">Styles <br> Conference</a>
  </h1>
  </section>
  <h3 class="tagline">August 24&ndash;26th &mdash; Chicago, IL</h3>

  
   <nav class="primary-nav">
    <a href="index.html" >Home</a>
    <a href="speakers.html">Speakers</a>
    <a href="schedule.html">Schedule</a>
    <a href="venue.html">Venue</a>
    <a href="register.html" >Register</a>
  </nav>

</header>
<section class="hero container">
  <h2>Dedicated to the Craft of Building Websites</h2>
  <p>Every year the brightest web designers and front-end developers descend on Chicago to discuss the latest technologies. Join us this August!</p>
   <a href="register.html" class="btn btn-alt">Register Now</a>
</section>

<section class="grid">
  <!-- Speakers -->
  <section class="teaser col-1-3">
  <a href="speakers.html">
    <h5>Speakers</h5>
    <h3>World-Class Speakers</h3>
      </a>
<p>Joining us from all around the world are over twenty fantastic speakers, here to share their stories.</</p>
</section><!--Schedule--><section class="teaser col-1-3">
  <a href="schedule.html">
    <h5>Schedule</h5>
    <h3>Three Inspiring Days</h3>
      </a>
<p>Enjoy three inspiring and action packed days of talks, gatherings and all-around goodtimes.</p>
</section><!--Venue--><section class="teaser col-1-3">
  <a href="venue.html">
    <h5>Venue</h5>
    <h3>The Chicago Theatre</h3>
      </a>
<p>Within the heart of downtown Chicago, The Chicago Theatre will provide a beautiful conference venue.</p></section>
</section>

<footer class="primary-footer container group">
  <small>&copy; Styles Conference</small>
  <a href="index.html">Home</a>
    <a href="speakers.html">Speakers</a>
    <a href="schedule.html">Schedule</a>
    <a href="venue.html">Venue</a>
    <a href="register.html">Register</a>
  </nav>
</footer>
</body>
</html>


/*
  ========================================
  Typography
  ========================================
*/

h1, h3, h4, h5, p {
  margin-bottom: 22px;
}

h1, h2, h3, h4 {
  color: #648880;
}

h1 {
  font-size: 36px;
  line-height: 44px;
}
h2 {
  font-size: 24px;
  line-height: 44px;
}
h3 {
  font-size: 21px;
}
h4 {
  font-size: 18px;
}

h5 {
  color: #a9b2b9;
  font-size: 14px;
  font-weight: 400;
}

.tagline {
  margin: 66px 0 22px 0;
}



/*
  ========================================
  Custom styles
  ========================================
*/
body {
  color: #888;
  font: 300 16px/22px "Open Sans", "Helvetica Neue", Helvetica, Arial, sans-serif;
}

strong {
  font-weight: 400;
}
cite, em {
  font-style: italic;
}

.hero {
  line-height: 44px;
  padding: 22px 80px 66px 80px;
}
.hero h2 {
  font-size: 36px;
}
.hero p {
  font-size: 24px;
}

/*
  ========================================
  Links
  ========================================
*/
.primary-nav {
  font-size: 14px;
  font-weight: 400;
}

a:hover {
  color: #a9b2b9;
}
a {
  color: #648880;
}

.teaser a:hover h3 {
  color: #a9b2b9;
}

Adding more to the footer too
  ========================================
  Primary footer
  ========================================
*/

.primary-footer {
  color: #648880;
  font-size: 14px;
  padding-bottom: 44px;
  padding-top: 44px;
}
.primary-footer small {
  float: left;
  font-weight: 400;
}

Applying Text Properties 

Text Align: 

