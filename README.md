# HTML & CSS Overview

## Introduction to My Web Development Journey

As part of my journey to become a software engineer, I am enrolled in the [100Devs bootcamp](https://100devs.org/), a free, community-driven program designed to equip aspiring developers with the skills needed for a career in software engineering. In the second class of this 30-week bootcamp, I focused on the fundamentals of HTML, learning how to structure content for the web effectively. To further enhance my skills, I am leveraging the comprehensive and beginner-friendly ["Learn to Code HTML & CSS" course by Shay Howe](https://learn.shayhowe.com/html-css/), which provides clear and organized lessons on both HTML and CSS, covering topics from basic semantics to advanced styling techniques like the box model and floats.

This GitHub repository represents the practical application of the knowledge I've gained from both the 100Devs bootcamp and Shay Howe's course. My goal is to build a strong foundation in web development by creating projects that demonstrate my ability to structure web pages with HTML and style them with CSS. This repository is the starting point for my next development arc, where I will continue to refine my skills, explore more complex web development concepts, and contribute to real-world projects.

The 100Devs bootcamp emphasizes not only technical skills but also community and collaboration, with a motto of "Be Kind, or Get The Fudge Out." Inspired by this ethos, I welcome feedback, suggestions, and collaboration from the 100Devs community and beyond as I work to improve my projects and grow as a developer. This repository will evolve as I progress through the bootcamp, incorporating new skills and showcasing my development journey.

Thank you for visiting my repository, and I look forward to sharing my progress as I continue to learn and build!

## Purpose
This repository serves as:
- A documentation of my progress through the 100Devs bootcamp, starting with HTML & CSS fundamentals from what I learned from HyperionDev.
- A showcase of practical HTML and CSS projects inspired by Shay Howe's course and personal initiatives.
- A reference for best practices in web development, applied to 100Devs assignments and real-world projects.
- A platform for collaboration and feedback from the 100Devs community and other developers.

## Contents
The repository includes guides and examples covering:
- **Typography**: Font properties, text alignment, web-safe fonts, and embedding custom fonts.
- **Backgrounds & Gradients**: Solid colors, images, linear/radial gradients, and multiple backgrounds.
- **Lists**: Ordered, unordered, and description lists with custom styling and navigation menus.
- **Media**: Embedding images, audio, video, and iframes with accessibility features and fallbacks.
- **Forms**: Accessible forms with inputs, labels, fieldsets, legends, and validation attributes.
- **Tables**: Structured tabular data with headers, captions, borders, and striping.
- **Best Practices**: Semantic HTML, modular CSS, organized syntax, and maintainable code.

Each section contains code snippets and examples demonstrating practical applications for 100Devs tasks and personal projects.

## Key Features
- **Semantic HTML**: Using elements like `<article>`, `<figure>`, and `<figcaption>` for accessibility and clarity.
- **Modular CSS**: Reusable classes, shorthand properties, and organized code with comments.
- **Accessibility**: Incorporating `alt` attributes, ARIA roles, and proper form labeling.
- **Responsive Design**: Examples optimized for various devices, inspired by modern frameworks.

## Example
A styled navigation menu from the repository, inspired by Shay Howe's lessons:
```html
<nav class="navigation">
  <ul>
    <li><a href="#">Profile</a></li>
    <li><a href="#">Settings</a></li>
    <li><a href="#">Notifications</a></li>
    <li><a href="#">Logout</a></li>
  </ul>
</nav>
```
```css
.navigation ul {
  font: bold 11px "Helvetica Neue", Helvetica, Arial, sans-serif;
  margin: 0;
  padding: 0;
  text-transform: uppercase;
}
.navigation li {
  display: inline-block;
}
.navigation a {
  background: linear-gradient(#49708f, #293f50);
  border-right: 1px solid rgba(0, 0, 0, 0.3);
  color: #fff;
  padding: 12px 20px;
  text-decoration: none;
}
```

## Resources
This repository draws from a variety of industry-standard resources to support my learning and project development:
- **HTML & CSS Learning**:
  - [100Devs Official Website](https://100devs.org/): Community-driven bootcamp.
  - [Shay Howe’s Learn to Code HTML & CSS](https://learn.shayhowe.com/html-css/): Beginner-friendly course.
  - [MDN Web Docs](https://developer.mozilla.org/en-US/): Comprehensive HTML and CSS documentation.
  - [HTML Dog](http://www.htmldog.com/): Beginner-friendly tutorials.
  - [Opera Dev](http://dev.opera.com/): Developer resources.
  - [DevDocs](http://devdocs.io/): Quick reference for web technologies.
- **Design Inspiration**:
  - [Dribbble](http://dribbble.com/): Creative design ideas.
  - [Premium Pixels](http://www.premiumpixels.com/): Free design resources.
- **Frameworks & Style Guides**:
  - [Web Style Guide](http://webstyleguide.com/wsg3/index.html): Principles for effective web design.
  - [Bootstrap](https://getbootstrap.com/): Responsive framework for rapid development.
  - [Foundation](http://foundation.zurb.com/): Flexible framework for responsive sites.
  - [Skeleton](http://getskeleton.com/): Lightweight CSS framework.
  - [Google HTML/CSS Style Guide](https://google.github.io/styleguide/htmlcssguide.html): Best practices for clean code.
  - [GitHub Style Guide](https://github.com/styleguide/): Code styling standards.
- **Icons**:
  - [Helveticons](http://helveticons.ch/): Premium icon sets.
  - [Yusuke Kamiyamane Icons](http://p.yusukekamiyamane.com/): Free icons.
  - [Pictos](http://pictos.cc/): Vector icon sets.
  - [The Noun Project](http://thenounproject.com/): Extensive icon library.
  - [Ionicons](http://ionicons.com/): Free, scalable icons.
  - [Silk Icons](http://www.famfamfam.com/lab/icons/silk/): Classic icon set.
  - [Picons](http://picons.me/): Premium icons for web design.
- **Miscellaneous**:
  - [Colour Lovers](http://www.colourlovers.com/): Color palettes and inspiration.
  - [ColorHexa](https://www.colorhexa.com/): Color information and tools.
  - [Modernizr](http://modernizr.com/): Feature detection for browser compatibility.
  - [jQuery](http://jquery.com/): JavaScript library for DOM manipulation.
  - [Google Hosted Libraries](https://developers.google.com/speed/libraries/devguide): CDN for common libraries.
  - [Copy Paste Character](http://copypastecharacter.com/): Special characters for web design.

## Contributions
I welcome feedback and collaboration from the 100Devs community and other developers! Please open an issue or submit a pull request for suggestions, bug fixes, or enhancements, especially for accessibility or cross-browser compatibility. Let’s build together, keeping with the 100Devs spirit of kindness and community.

## Acknowledgments
- **100Devs**: For an inspiring, supportive learning environment and community-driven curriculum.
- **Shay Howe**: For a clear and structured HTML/CSS course that complements my bootcamp learning.
- **Open-Source Community**: For the wealth of resources that fuel this project.

## Key Citations
- [100Devs Official Website](https://100devs.org/)
- [Shay Howe’s Learn to Code HTML & CSS](https://learn.shayhowe.com/html-css/)
- [100Devs Class 2 Curriculum on GitHub](https://github.com/NP558565/100devs)

Explore the repository for detailed guides and code samples, and follow my journey as I grow as a web developer!


