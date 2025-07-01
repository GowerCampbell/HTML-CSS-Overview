# HTML & CSS Fundamentals

This repository documents my learning journey through HTML and CSS, starting with my initial studies at **HyperionDev** and now continuing with the intensive **[100Devs](https://100devs.org/)** bootcamp. It serves as a public archive of my notes, projects, and progress.

---

## 🎯 Purpose of This Repository

This repository is a living document of my web development education. Its primary goals are to:

- **Track Progress:** Chronicle my learning from HyperionDev and the 100Devs curriculum.
- **Showcase Projects:** Display practical HTML & CSS work inspired by courses and personal challenges.
- **Reinforce Learning:** Act as a reference for best practices in semantic HTML, modular CSS, and accessibility.
- **Foster Collaboration:** Invite feedback and contributions from the 100Devs community and other developers.

## 📚 Learning Notes & Key Takeaways

I believe in learning in public. Here are my structured notes from the foundational courses that have shaped this repository.

- **CSS Fundamentals**
  - Notes from the [Learn Layout](https://learnlayout.com/) tutorial, covering the box model, positioning, and Flexbox.
  - **[➡️ View Notes: CSS-Fundamental-Notes.md](Learn-Layouts/CSS-Fundamental-Notes.md)**

- **Developing Stylish Websites**
  - Takeaways from Shay Howe's ["Learn to Code HTML & CSS"](https://learn.shayhowe.com/html-css/), focusing on building a complete website from scratch.
  - **[➡️ View Notes: building-your-first-website.md](develop-style-websites/building-your-first-website.md)**
 
- **Learn Layouts**
    -  ["Learning Layouts"](https://learnlayout.com/), focusing on building the structure behind HTML for websites.
    - **[➡️ View Notes: HTML Layout-Notes](Learn-Layouts/CSS-Fundamental-Notes.md)**

## 🛠️ Core Concepts & Contents

This repository contains guides and practical examples covering the following areas:

| Category | Topics Covered |
| :--- | :--- |
| **Typography** | Font properties, text alignment, web-safe fonts, and embedding custom fonts. |
| **Backgrounds & Gradients** | Solid colors, images, linear/radial gradients, and multiple backgrounds. |
| **Structure & Layout** | Lists, media embedding (images, audio, video), accessible forms, and data tables. |
| **Best Practices** | Semantic HTML, modular CSS, organized syntax, and maintainable code. |
| **Accessibility** | `alt` attributes, ARIA roles, proper form labeling, and other accessibility features. |
| **Responsive Design** | Examples optimized for various devices, inspired by modern frameworks. |

### Code Example: Styled Navigation Menu

Here is a sample of a styled navigation menu from the repository, inspired by Shay Howe's lessons.

```html
<nav class="navigation">
  <ul>
    <li><a href="#">Profile</a></li>
    <li><a href="#">Settings</a></li>
    <li><a href="#">Notifications</a></li>
    <li><a href="#">Logout</a></li>
  </ul>
</nav>
````

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

## 🤝 Contributions & Community

Feedback and collaboration are welcome\! In the spirit of the 100Devs community, feel free to open an issue or submit a pull request for suggestions, bug fixes, or enhancements.

## 🙏 Acknowledgments

  - **100Devs:** For an inspiring, supportive, and community-driven learning environment.
  - **Shay Howe:** For a clear and structured HTML/CSS course that perfectly complements my bootcamp learning.
  - **The Open-Source Community:** For the wealth of incredible resources that make this journey possible.

-----

## 🔗 Resources & Tools

<details>
<summary><strong\>Click to view the full list of learning resources, tools, and inspiration</strong></summary>

### HTML & CSS Learning

  - [100Devs Official Website](https://100devs.org/): Community-driven bootcamp.
  - [Shay Howe’s Learn to Code HTML & CSS](https://learn.shayhowe.com/html-css/): Beginner-friendly course.
  - [MDN Web Docs](https://developer.mozilla.org/en-US/): Comprehensive HTML and CSS documentation.
  - [HTML Dog](http://www.htmldog.com/): Beginner-friendly tutorials.
  - [Opera Dev](http://dev.opera.com/): Developer resources.
  - [DevDocs](http://devdocs.io/): Quick reference for web technologies.

### Design Inspiration

  - [Dribbble](http://dribbble.com/): Creative design ideas.
  - [Premium Pixels](http://www.premiumpixels.com/): Free design resources.

### Frameworks & Style Guides

  - [Web Style Guide](http://webstyleguide.com/wsg3/index.html): Principles for effective web design.
  - [Bootstrap](https://getbootstrap.com/): Responsive framework for rapid development.
  - [Foundation](http://foundation.zurb.com/): Flexible framework for responsive sites.
  - [Skeleton](http://getskeleton.com/): Lightweight CSS framework.
  - [Google HTML/CSS Style Guide](https://google.github.io/styleguide/htmlcssguide.html): Best practices for clean code.
  - [GitHub Style Guide](https://github.com/styleguide/): Code styling standards.

### Icons

  - [Helveticons](http://helveticons.ch/): Premium icon sets.
  - [Yusuke Kamiyamane Icons](http://p.yusukekamiyamane.com/): Free icons.
  - [Pictos](http://pictos.cc/): Vector icon sets.
  - [The Noun Project](http://thenounproject.com/): Extensive icon library.
  - [Ionicons](http://ionicons.com/): Free, scalable icons.
  - [Silk Icons](https://www.google.com/search?q=http.famfamfam.com/lab/icons/silk/): Classic icon set.
  - [Picons](http://picons.me/): Premium icons for web design.

### Miscellaneous

  - [Colour Lovers](http://www.colourlovers.com/): Color palettes and inspiration.
  - [ColorHexa](https://www.colorhexa.com/): Color information and tools.
  - [Modernizr](http://modernizr.com/): Feature detection for browser compatibility.
  - [jQuery](http://jquery.com/): JavaScript library for DOM manipulation.
  - [Google Hosted Libraries](https://developers.google.com/speed/libraries/devguide): CDN for common libraries.
  - [Copy Paste Character](http://copypastecharacter.com/): Special characters for web design.

</details>


## Contributions
I welcome feedback and collaboration from the 100Devs community and other developers! Please open an issue or submit a pull request for suggestions, bug fixes, or enhancements, especially for accessibility or cross-browser compatibility. Let’s build together, keeping with the 100Devs spirit of kindness and community.

## Acknowledgments
- **HyperionDev**: Starting my journey forward into a new skillset.
- **100Devs**: For an inspiring, supportive learning environment and community-driven curriculum.
- **Shay Howe**: For a clear and structured HTML/CSS course that complements my bootcamp learning.
- **Open-Source Community**: For the wealth of resources that fuel this project.

## Key Citations
- [100Devs Official Website](https://100devs.org/)
- [Shay Howe’s Learn to Code HTML & CSS](https://learn.shayhowe.com/html-css/)

Explore the repository for detailed guides and code samples, and follow my journey as I grow as a web developer!


